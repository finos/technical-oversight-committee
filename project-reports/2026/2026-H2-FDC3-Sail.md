# FDC3 Sail - Semi-Annual Report 2026 H2

**Project Maintainers:**

| GitHub Username | Name         | Organization  | Email                       |
| --------------- | ------------ | ------------- | --------------------------- |
| @SeeWhatsOn     | Chris Watson | Elgin White   | cwatson1988@gmail.com       |
| @kriswest       | Kris West    | NatWest Group | kristopher.west@natwest.com |
| @robmoffat      | Rob Moffat   | FINOS         | rob.moffat@finos.org        |

**Repository:** https://github.com/finos/FDC3-Sail

**Links:**

- [User guide](https://github.com/finos/FDC3-Sail/blob/main/docs/GUIDE.md). The published docs site is offline; see Challenges.
- [PR #341](https://github.com/finos/FDC3-Sail/pull/341), the v3 release, open at time of writing
- [LFX Insights](https://insights.linuxfoundation.org/project/electron-fdc3), still under the pre-rename `electron-fdc3` slug
- [OpenSSF Scorecard](https://scorecard.dev/viewer/?uri=github.com/finos/FDC3-Sail), currently 7.9

> _First report under the semi-annual process. Lifecycle: **Incubating**. Licence: Apache-2.0. Figures are measured from the GitHub API and the git history of `finos/FDC3-Sail` as at 26 August 2026, except where marked as LFX Insights._

# Project Overview

FDC3 Sail is FINOS's open source implementation of the [FDC3](https://fdc3.finos.org) interoperability standard.

**Today's released version is v2**, a web-based MVP that was never intended for production use. **v3 is the direction of travel** and is open now as [PR #341](https://github.com/finos/FDC3-Sail/pull/341): a browser-first FDC3 2.2 Desktop Agent (`@finos/sail-desktop-agent`), a composition layer (`@finos/sail-platform`), and two example UI shells, `sail-finance` and `sail-one`. v3 is the release that puts Sail on npm for the first time. It lands in stages: the alpha merges to `main` in September, a beta follows in October, and v3 is demoed at OSFF New York in November.

The short version of this cycle: the project went from one contributor to three maintainers and six contributors, deleted its Electron attack surface, measured its security posture for the first time, and prepared v3. It now needs reviewers and real-world adopters.

## How Sail got here

| Period   | What happened                                                                        |
| -------- | ------------------------------------------------------------------------------------ |
| Feb 2022 | Started as `electron-fdc3`, an Electron FDC3 container, by Nick Kolba                |
| 2023     | Handed over to Rob Moffat                                                            |
| **2024** | **Rob was the only contributor. 130 commits, one person, no bus factor.**            |
| 2025     | Rebuilt for the web; v2 ships. Chris Watson's first commit lands in May.             |
| **2026** | **Kris West joins. Three maintainers and six contributors, matching the 2022 peak.** |

The work of this period was to make Sail sturdy rather than to add features. v3 finishes what the rename from `electron-fdc3` started: browser-first, no server component, published to npm. Sail targets full FDC3 2.2 conformance today.

The goal is **production-ready software while remaining Incubating this cycle.**

# Current Status

**Adoption and validation**

- **First use outside the maintainer group.** Sail's Desktop Agent ran in a live proof-of-concept with a buy-side firm between April and June 2026 and performed as expected. The firm cannot be named publicly, but details can be shared privately with the TOC liaison.
- **v3 makes adoption a-la-carte.** The release PR opened on 24 August 2026. Adopters can take just the Desktop Agent package, take `sail-platform`, or clone the repository and customise a UI shell.
- **Demoed against third-party FDC3 apps.** Sail has been shown working with FDC3 apps it does not own, including AdapTable, which is carried in the app directory. These demos have not yet been written up publicly; see Challenges.
- **Sail and the FDC3 standard share their maintainers.** All three Sail maintainers are also maintainers of the FDC3 standard, and Kris West is its lead maintainer. That overlap positions Sail as a reference and conformance-testing implementation for FDC3 3.0.

**Engineering**

- **Electron removed entirely.** The `sail-electron` package was deleted, eliminating a critical `nodeIntegration` and RCE exposure.
- **Security tooling tightened and updated.** CodeQL, OpenSSF Scorecard, OpenSSF Best Practices (CII 12272, currently _passing_), Semgrep, dependency review, Node.js CVE scanning, a weekly OSPS Baseline assessment, and a Changesets release pipeline.
- **Dense regression coverage.** 85 Vitest files across the monorepo, 60 of them in the agent, plus 17 Cucumber features covering 154 scenarios, with a tag-coverage check that fails the build if FDC3 spec tags go untested.

# Community & Contribution Metrics

## Growth

The maintainer group **tripled**, from one to three. New this period: **2 maintainers** (Kris West and Chris Watson) and **3 new contributors**, with **100% retention** of the prior quarter's contributors. 2026 has already matched the project's best-ever contributor count with four months still to run.

| Year             | Active human contributors |          | Commits to `main` |
| ---------------- | ------------------------- | -------- | ----------------- |
| 2022             | 6                         | `██████` | 244               |
| 2023             | 5                         | `█████`  | 133               |
| 2024             | **1**                     | `█`      | 130               |
| 2025             | 3                         | `███`    | 78                |
| 2026 (to 26 Aug) | **6**                     | `██████` | 21                |

The 2026 commit column is not a slowdown. The v3 rewrite arrives as a single pull request carrying **819 changed files and roughly 513,000 added lines across two commits**, none of which is on `main` yet.

Figures cover commits on `main` only, excluding merge commits, with bot and agent authors removed and duplicate author identities merged.

**Stars are the weak signal.** 48 in total, and the yearly pattern shows attention has never recovered to the 2022 launch spike. Growing this is a stated goal.

| Year | New stars |                      |
| ---- | --------- | -------------------- |
| 2022 | 18        | `██████████████████` |
| 2023 | 6         | `██████`             |
| 2024 | 11        | `███████████`        |
| 2025 | 5         | `█████`              |
| 2026 | 8         | `████████`           |

## Where the project is strong, and where it is not

LFX Insights scores Sail **77 out of 100, "healthy"**. The dimension breakdown is the clearest single picture of this reporting period.

| LFX health dimension | Score  |                      |
| -------------------- | ------ | -------------------- |
| Security             | **86** | `█████████████████▏` |
| Development          | 72     | `██████████████▍`    |
| Popularity           | 50     | `██████████`         |
| Contributor          | 40     | `████████`           |
| **Maintainer**       | **37** | `███████▍`           |

**Security is the strongest dimension and maintainer capacity the weakest.** The hardening work has landed. The bandwidth to keep landing it has not. That is the ask in this report.

## Throughput

| Metric                                 | Value                                    |
| -------------------------------------- | ---------------------------------------- |
| Issues opened / closed, last 12 months | 112 / **92** (82% closed)                |
| PRs opened / merged, last 12 months    | 44 / **25**                              |
| Open issues / open PRs                 | 36 / **9**                               |
| Median first response on a PR          | **~10 hours**                            |
| Median time to merge a PR              | 7 days                                   |
| Median time to close an issue          | 35 days                                  |
| Distinct human contributors, lifetime  | 14                                       |
| Stars / forks                          | 48 / 39                                  |
| OpenSSF Scorecard                      | **7.9**                                  |
| npm downloads                          | none yet; first alpha publishes Sep 2026 |

**Sail answers quickly and finishes most of what it starts.** A pull request gets a first response in about ten hours, and 82% of the issues raised get closed. What three people cannot do is review at volume, and that is where work stalls. Nine pull requests are open as this is written, including security fixes that cannot merge until another maintainer reviews them.

**Other signals:** 100% quarter-over-quarter contributor retention, 93 active days out of 365, 26% of contributions made outside standard working hours, and meetings every two weeks on LF Zoom with attendance typically of three or four, tracked as issues labelled `meeting`.

## OSPS Baseline position

The weekly assessment workflow had been reporting success while producing no assessment. It passed a repository secret that does not exist, so despite a green tick **no maturity level had ever been evidenced**. The fix is [#343](https://github.com/finos/FDC3-Sail/pull/343). Running the scanner (catalog `osps-baseline-2026-02`) against `main` on 25 August 2026 gives the real position.

| Maturity level                   | Passed | Needs review | Failed |
| -------------------------------- | ------ | ------------ | ------ |
| Level 1                          | 12     | 2            | **3**  |
| Level 2, required for Incubating | 16     | 7            | **6**  |

| Level 2 failure | Gap                                        | Closes via                                                           |
| --------------- | ------------------------------------------ | -------------------------------------------------------------------- |
| `OSPS-DO-01`    | User guide not declared                    | [#343](https://github.com/finos/FDC3-Sail/pull/343), awaiting review |
| `OSPS-QA-04`    | Repository list not declared               | [#343](https://github.com/finos/FDC3-Sail/pull/343), awaiting review |
| `OSPS-QA-05`    | `.DS_Store` committed at repository root   | [#343](https://github.com/finos/FDC3-Sail/pull/343), awaiting review |
| `OSPS-VM-03`    | No private reporting contact; PVR disabled | [#342](https://github.com/finos/FDC3-Sail/pull/342); PVR requested   |
| `OSPS-QA-03`    | Six status checks run, none mandatory      | Maintainers to make them required, September 2026                    |
| `OSPS-DO-06`    | No dependency management policy            | Policy to be written, Q4 2026                                        |

Four of the six stem from a missing `security-insights.yml`. #343 adds one and closes three. **Level 1 clears entirely once that pull request merges.**

Two Level 1 controls, `OSPS-AC-03` for branch protection and `OSPS-BR-07` for secret scanning, sit at _needs review_ rather than failing. `main` is protected, but the scanner's token cannot read repository settings, so it cannot confirm the configuration. LFX Insights hits the same wall and records `branchProtectionEnabled` as null. Moving `main` from classic branch protection to a repository ruleset would make the configuration readable to both tools.

# Challenges & Blockers

The maintainers would rather state these plainly than have them surfaced during the review.

1. **Review capacity is the bottleneck, and it is the primary risk.** Three maintainers, nine open pull requests, and security fixes that cannot land until a maintainer reviews them.
2. **Contribution concentration.** One contributor accounts for **58% of all commits** to `main` over the project's lifetime, and LFX puts organisational concentration at a similar level with a bus factor of 3. The goal is to diversify beyond NatWest, FINOS and Elgin White rather than simply to add a fourth organisation.
3. **Dependency vulnerabilities, now in hand.** `npm audit` against `main` on 25 August 2026 reported 11 advisories in production dependencies, down from 25 earlier that month. [#346](https://github.com/finos/FDC3-Sail/pull/346) clears every critical and high severity finding and is open for review. OpenSSF Scorecard still reads 0 out of 10 on Vulnerabilities, but that scan is dated 17 August and predates this work.
4. **Vulnerability reporting is not yet private.** `SECURITY.md` directs reporters to open a public issue. A rewrite aligning with the [FINOS responsible disclosure policy](https://community.finos.org/docs/governance/software-projects/cve-responsible-disclosure) is open as [#342](https://github.com/finos/FDC3-Sail/pull/342), and private vulnerability reporting has been requested from FINOS.
5. **External integrations are demoed but not written up.** Sail has been demoed against third-party FDC3 apps, including AdapTable, which is carried in the app directory. What the project lacks is a published, citable account of one of those integrations that a prospective adopter could read. Producing one is a roadmap goal for this period.
6. **Not yet published to npm.** The first alpha packages publish in September 2026, so there is no downloads signal to point to in this report.
7. **Two long-lived pull requests.** [#312](https://github.com/finos/FDC3-Sail/pull/312), the WSCP implementation open since June, will be carried forward onto v3. [#238](https://github.com/finos/FDC3-Sail/pull/238), enhanced config screens open since March, is superseded by the v3 rewrite and will be closed with an explanation to its author.
8. **The documentation site is not live yet.** The guides have been rewritten and a publishing workflow ships with v3, but GitHub Pages is not yet enabled, so `finos.github.io/FDC3-Sail/` still returns 404 and the guides are readable only in the repository. This resolves when v3 merges.
9. **Tracking a moving standard.** Sail implements FDC3 3.0 behaviour ahead of the standard's own release, so parts of the 3.0 surface are hand-maintained until upstream `@finos/fdc3` ships them.
10. **Stale LFX slug and tags.** The display name is correct, but the URL slug is still `electron-fdc3` and the project is tagged `electron` and `fdc3`, for a project whose headline this cycle is that Electron has been removed.

# Roadmap & Goals for Next 6 Months

| When            | Goal                                                                           |
| --------------- | ------------------------------------------------------------------------------ |
| **Sep 2026**    | **Merge the v3 alpha into `main`** and publish the first alpha packages to npm |
| Sep 2026        | Land the open security PRs, clear dependency advisories, clear OSPS Level 1    |
| Sep 2026        | Bring the documentation site live once Pages is enabled                        |
| **Oct 2026**    | **v3 beta release**                                                            |
| **Nov 2026**    | **Demo Sail v3 at OSFF New York**                                              |
| Nov-Dec 2026    | Produce one citable external integration story, on the beta                    |
| Sep 2026        | Label a first tranche of `good first issue` and `help wanted` tickets          |
| Q4 2026         | Onboard one actively contributing organisation                                 |
| **Next report** | **Evidence OSPS Baseline Maturity Level 2**                                    |
| Ongoing         | Track FDC3 3.0 to completion; build v3 momentum with launch webinars           |

By "actively contributing organisation" the maintainers mean sustained enough participation in issues, pull requests and reviews to justify electing a maintainer from that organisation.

# TOC Support Needed

**The direct ask:**

**Send us reviewers.** This is the single most useful thing the TOC can offer. Three maintainers cannot review their own work at the volume the project now generates, and pull requests including security fixes are queued behind review rather than behind effort. Maintainer-level reviewers from other FINOS projects, or FINOS staff time, would move more than any other intervention. [#342](https://github.com/finos/FDC3-Sail/pull/342), [#343](https://github.com/finos/FDC3-Sail/pull/343) and [#346](https://github.com/finos/FDC3-Sail/pull/346) are open and waiting as this report is written.

**And the longer-running asks:**

1. **Help us get Sail running in real environments.** Introductions to member firms evaluating FDC3 desktop agents, and help converting current inbound interest into named evaluations. NatWest is the most likely first candidate given Kris West's involvement, and the maintainers would welcome help making that concrete.
2. **A call for contributors through FINOS channels and the newsletter**, plus community management support for growing meeting attendance beyond the current three or four. The project has regular meetings and a labelled on-ramp; what it lacks is reach.
3. **Visibility, anchored on OSFF New York.** The maintainers plan to demo v3 there in November, and would welcome help amplifying that demo, the v3 launch and the NatWest maintainer addition around the event.
4. **Cross-project collaboration.** FDC3, FDC3 Sail and Backplane present in the same session. Given that all three Sail maintainers also maintain the FDC3 standard, the maintainers would like to discuss a joint story: Sail as the reference and conformance-testing implementation for FDC3 3.0, with Backplane covering bridging.
5. **Lifecycle guidance.** To be explicit, because "production grade" is easy to misread as a lifecycle claim: the maintainers are aiming for **production-ready software while remaining Incubating**, with v3 as the marker. Their view is that the path to Graduated then runs through the npm release, named production adopters and OSPS Baseline Level 3. They would welcome the TOC's view on what evidence a graduation review would need.

# Additional Information

- **Monorepo, using npm workspaces:** `sail-desktop-agent` for the Desktop Agent core, `sail-platform` for composition, `sail-theme` for shared design tokens, `sail-finance` and `sail-one` as example shells, `sail-conformance-harness`, and a Docusaurus documentation site.
- **Version history:** **v1** was the Electron proof-of-concept, **v2** the current web MVP not aiming for production, and **v3** the server-free browser UI packaged for a-la-carte adoption.
- **Contribution model:** pull request based, with CI gates covering format, build, lint, typecheck, unit tests, Cucumber conformance scenarios and a docs build.
