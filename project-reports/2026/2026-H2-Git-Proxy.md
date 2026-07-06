# GitProxy - Semi-Annual Report  [2026 H2]

**Project Maintainers:**

| GitHub Username | Name          | Organization                       | Email                       |
| --------------- | ------------- | ---------------------------------- | --------------------------- |
| @06kellyjac     | Jack Kelly    | @controlplaneio                    | jack+finos@control-plane.io |
| @andypols       | Andy Pols     | Qube Research & Technologies (QRT) | andrew.pols@qube-rt.com     |
| @coopernetes    | Thomas Cooper | @RBC                               | thomas.cooper@rbc.com       |
| @grovesy        | Paul Groves   | Citi                               | paul.groves@citi.com        |
| @jescalada      | Juan Escalada | G-Research Open Source Software    | juan.escalada@gr-oss.io     |
| @kriswest       | Kris West     | NatWest Group                      | kristopher.west@natwest.com |

**Repository:** https://github.com/finos/git-proxy

# Project Overview

GitProxy is an application that stands between developers and a Git remote endpoint (e.g., github.com). It applies rules and workflows (configurable as plugins) to all outgoing git push operations to ensure they are compliant.

## Goals for H2 2026
- Increase contributor/contribution counts
- Speed up PR reviews and merge speeds
- Release GitProxy 2.1 and 2.2, including SSH support and brand-new UI

# Current Status

## Key accomplishments

Source: [LFX Insights](https://insights.linuxfoundation.org/project/git-proxy/repository/finos_git-proxy/contributors)
- Consistently achieved 10+ participants in our bi-weekly Community Calls
- Increased contributor count from 15/16 in Q3/Q4 '25 to 26 in Q2 '26
- Increased star count by 26% from 193 to 245

## Major milestones achieved

- Released GitProxy v2 with many improvements including: support beyond GitHub, better handling of fork-based workflows, improved performance for large repositories, clearer documentation and better user experience
- Deployed to Docker Hub gaining additional exposure
- Added [architecture guide](https://git-proxy.finos.org/docs/architecture/) and [user manual](https://git-proxy.finos.org/docs/user-manual) to improve onboarding process

## New features delivered

Features merged to main but not yet released:
- SSH push support https://github.com/finos/git-proxy/pull/1332
- Upstream proxy support https://github.com/finos/git-proxy/pull/1458
- Support for pushing annotated tags https://github.com/finos/git-proxy/pull/1139

# Community & Contribution Metrics

## Contributors (new/active)

<img width="738" height="609" alt="image" src="https://github.com/user-attachments/assets/fe91ad4f-d403-42f4-815f-1d858f0b07c8" />

## Downloads/adoption indicators
3.8K cumulative downloads on [Docker Hub](https://hub.docker.com/r/finos/git-proxy) since first deployed in January
625 peak [weekly package downloads](https://www.npmjs.com/package/@finos/git-proxy) on NPM (82% increase from previous peak of 344 in H2 2025)

## PR metrics

## H1 2026

Compared to H2 2025, our PR merge speed has nearly doubled:

<img width="743" height="594" alt="image" src="https://github.com/user-attachments/assets/e4781a10-ced3-4db3-9e5f-5e697669edbf" />

## H2 2025 (for reference)

<img width="743" height="594" alt="image" src="https://github.com/user-attachments/assets/9e5d5e0f-5093-4bef-a991-82ff9e9dec56" />

## Other metrics
- Open PRs: 44
- Open Issues: 72

# Challenges & Blockers

## Tech debt

A lot has been done in the past year to clean up tech debt (full TypeScript refactor, test coverage raised from 60% to 90%, OpenSSF scorecard score raised to 9.0, etc.).

The UI is undergoing a [large-scale refactor](https://github.com/finos/git-proxy/pull/1507) to be released in 2.2. However, we still have to improve API type safety, and deeper architectural reforms to support new features.

## Community or adoption barriers

We're currently working on marketing GitProxy along with FINOS in hopes of getting new contributors and future maintainers onboard. It's not entirely clear what the target audience should be, so we would appreciate any examples of successful marketing campaigns for other projects. 

# Roadmap & Goals for Next 6 Months
- Goal: Onboard 1 new actively contributing organization (financial firm or otherwise)
  - By "actively contributing", we mean active in making issues, PRs and reviews, enough to elect a new maintainer from that organization
  - An organization may assign multiple developers to the project
- Upcoming milestones/releases
  - GitProxy 2.1 (SSH Release + various other features)
  - GitProxy 2.2 (Full UI revamp)
- Planned features
  - Porting various QoL features from [fogwall](https://github.com/RBC/fogwall) including:
    - Real-time feedback on pushes https://github.com/finos/git-proxy/pull/1637
    - Deferred forwarding of approved pushes (for long-running checks)
    - In-process credential handling to skip double-push requirement
    - Client disconnect detection

# TOC Support Needed

As GitProxy matures, we find ourselves needing more people to help us review PRs and make minor improvements that maintainers often don't have the time to do. Therefore, we'd really appreciate any support in getting GitProxy out in the world.

We're also open to collaborating with other FINOS or LF projects that could benefit from including GitProxy as a dependency or to solve a specific problem.

# Additional Information
@coopernetes recently contributed [Fogwall](https://github.com/RBC/fogwall), a Java reimplementation of GitProxy that [solves some pain points](https://gist.github.com/coopernetes/d02d48efa759282ff8187da0d5dcae64) specific to his organization. We're working on [porting some of those features](https://github.com/finos/git-proxy/issues/1638) into GitProxy.
