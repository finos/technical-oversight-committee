# OpenGRIS - Semi-Annual Report [2026 H2]

**Project Maintainers:**

| GitHub Username | Name           | Email                              |
| --------------- | -------------- | ---------------------------------- |
| @e117649        | Eric Lesiuta   | eric117649@gmail.com               |
| @magniloquency  | George Lewis   |                                    |
| @rafa-be        | Raphael Javaux | raphael@noisycamp.com              |


**Repositories:**

- https://github.com/finos/opengris-scaler
- https://github.com/finos/opengris-parfun
- https://github.com/finos/opengris-pargraph

> _Metrics below are drawn from GitHub over the trailing-6-month window (2025-04-16 → 2026-10-16), which spans this H2 reporting period

# Project Overview

OpenGRIS is a collection of 3 projects enabling easy parallelization of Python computations.

- Scaler, a distributed computing orchestrator for running Python tasks across machines or clouds.
- Parfun, a lightweight Python library making it easy to parallelize Python functions.
- Pargraph, a lightweight parallel graph computation library for Python.

# Current Status

- **Improved stability** over complex, production-grade computations (v2.8.0).
- Initial release of our **multi-cloud auto-scaling framework**
    - Support for AWS, IBM Symphony, OCI (Oracle) merged or in review
- **New low-level network stack** (YMQ / C++):
    - Improved performance.
    - Lower memory usage (zero-copy task scheduling).
- **Launchpad**: a web launched setup wizard for AWS, IBM Symphony, OCI (Oracle)...
- Misc:
    - SSL support
    - Improved support for macOS/Windows
    - New GUI
    - More resilient internal state-machine
    - ...

# Community & Contribution Metrics

All metrics for OpenGRIS-Scaler over the past 6 months:

- 12 contributors but mostly concentrated among project maintainers (91%).
- 157 PRs merged, 12 open (non-draft).
- 68 open issues, 70 closed.
- PyPI downloads (last 30 days): 6,086

# Challenges & Blockers

- **Technical**:
    - Efficient auto-scaling is challenging: rebalancing of tasks, downscaling, reliability...
    - Don't break existing features
- **Adoption**:
    - Create awareness
    - Be more community-active, e.g. conferences, social media...

# Roadmap & Goals for Next 6 Months

- Short term (v3.0.0, November 2026):
    - **Production-ready multi-cloud auto-scaling**
- Long term:
    - **Improved adoption**: more community engagement, more conferences (OSFF NYC, API-Days Paris)...
    - **"Unified" distributed scheduling** vs existing centralized task scheduling architecture
    - **Improved testing**
    - **Benchmarking** and performance tuning

# TOC Support Needed

**Help OpenGRIS promote the project, increasing adoption.**

OpenGRIS is maturing and we are getting more confident promoting it. FINOS can help improve the project visibility
with partners (conferences) and/or enabling cross-project collaboration.