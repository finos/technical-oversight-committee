# Legend - Semi-Annual Report  2026 H2

**Project Maintainers:**

- Adam Fine
- Aitana Myohl
- Andrew Ormerod
- Aziem Chawdhary
- Beeke-Marie Nelke
- Bella Wiseman
- David Harte
- Gunjan Shah
- Ivan Kyosev
- John Pentelow
- Kevin Knight
- Mauricio Uyaguari
- Mimi Tam
- Mohammed Ibrahim
- Rafael Bey-Hernandez
- Rohit Pant

**Links:**

- Umbrella / documentation: https://github.com/finos/legend
- Legend Studio (Studio, Query, DataCube, Marketplace, Pure IDE, REPL): https://github.com/finos/legend-studio
- Legend Engine: https://github.com/finos/legend-engine
- Legend Pure: https://github.com/finos/legend-pure
- Legend SDLC: https://github.com/finos/legend-sdlc
- Legend Depot: https://github.com/finos/legend-depot
- Legend Shared: https://github.com/finos/legend-shared
- PyLegend (Python client): https://github.com/finos/pylegend
- Legend Engine IDE LSP / VS Code client: https://github.com/finos/legend-engine-ide-lsp · https://github.com/finos/legend-engine-ide-client-vscode
- Documentation site: https://legend.finos.org · FINOS-hosted shared instance: https://legend.finos.org/studio

> _Metrics below are drawn from the GitHub API and from [LFX Insights for Legend](https://insights.linuxfoundation.org/project/legend), plus the npm and Docker Hub registries. The primary window is the trailing 12 months (**2025-07-30 → 2026-07-30**), which spans this H2 reporting period and the preceding half, with an inner 6-month window (**2026-01-30 → 2026-07-30**) where a shorter view is more informative. Every figure is attributed to its source, because GitHub-derived and LFX-derived aggregates window and de-duplicate differently and will not match. Lifecycle stage: **Incubating** since 2020-10-19 (accepted 2020-01-30). License: **Apache-2.0**._

# Project Overview

Legend provides an **end-to-end data platform experience covering the full data lifecycle**. It is a suite of data management and governance components — the **Legend Platform** — designed to break down silos and bridge the historical divide between business and engineering, so that firms can build data-driven applications and business intelligence on a shared, governed model. Legend was originally developed by Goldman Sachs and contributed to FINOS in **October 2020**.

Legend's distinguishing capabilities are consistent data vocabularies; self-service retrieval of data that respects the entitlements of the underlying sources; formal governance constructs for ownership, validation and provenance; and code generation to JSON Schema, Protobuf and AVRO for interoperability across models and systems.

The platform is built around:

- **[Legend Studio](https://github.com/finos/legend-studio)** — the visual data modelling environment. The `legend-studio` monorepo now ships a materially broader surface than the umbrella README describes: **Studio, Query, DataCube, Marketplace, Pure IDE and REPL**.
- **[Legend Engine](https://github.com/finos/legend-engine)** — the execution engine that compiles models to native queries and pushes execution down to the underlying stores.
- **[Legend SDLC](https://github.com/finos/legend-sdlc)** — model change management, backed by GitLab.
- **[Legend Depot](https://github.com/finos/legend-depot)** — the model artifact repository and dependency resolver.
- **[Legend Pure](https://github.com/finos/legend-pure)** — an immutable functional language based on UML and inspired by the Object Constraint Language (OCL), in which models and queries are expressed.
- **[PyLegend](https://github.com/finos/pylegend)** — a Python client offering interactive query building and push-down execution against the Legend ecosystem.

# Current Status

Development across the period was concentrated in eight themes. Version movement over the 6-month window: **Engine 4.118.6 → 4.137.0**, **Pure 5.74.1 → 5.91.0**, **SDLC 0.216.0 → 0.230.0**, **Depot 2.86.1 → 2.95.0**, **Shared 0.31.3 → 0.36.0-RC2**, and **PyLegend 0.13.0 → 1.1.3, reaching its first stable 1.0.0 on 2026-04-24**. Engine and SDLC maintain parallel maintenance branches, so tag sequences interleave rather than advancing linearly.

- **Legend SQL / Pure2SQL** — the single largest theme, with 30+ merged changes: lateral queries, `distinct` over multi-argument functions, `current_user`, JSON build functions, coalesce-relation and LIKE escape characters, window functions without a frame end, variant column types in result sets, Postgres `DateDiff` and lateral grammar, plus an **end-to-end SQL parity test framework**, connection pooling with defensive connection management, and improved thread management.
- **Relation / TDS 2.0** — relation mapping union; sub-aggregation and correlated subqueries with `GROUP BY` for Relation Function Class Mappings; enum and inline/embedded mappings for class-to-relation; relation data in mapping test suites; and **Arrow IPC** as a serialization format.
- **Pure language** — **multi-line string literals** with Java text-block semantics; an **LSP implementation for Pure**; **PELT metadata** replacing the previous distributed metadata format across both Engine and Pure; **ModelJoins** support in the language and compiler; stereotypes and tagged values on Columns and ColSpecs; migration of the PCT test framework to "surveyor".
- **Data Quality & Reconciliation** — a **net-new capability** this period, spanning Engine (recon grammar, plan-generation and enrichment APIs, DQ persistence strategy grammar) and Studio (DQ validation query form, validation suggestions, recon grammar and forms, plan generation), with authored documentation.
- **Legend AI / MCP** — an **MCP server** wired into service registration in Query; **LLM integration in Marketplace** across data products and data spaces; AI-generated query titles and descriptions; inline documentation suggestions on services; a Copilot-style inline chat agent; and telemetry plus usage analytics for the assistant. `AGENTS.md` guides were added for AI agents working in the codebase.
- **Studio UX** — the **light theme was completed and enabled in production** (2026-07-11), with semantic-token mapping for the legacy light theme; typed-TDS window functions in Query Builder (`rank()`, `rowNumber()`, `percentRank()`, aggregate windows); relation and accessor querying; a cell-selection statistics bar with asynchronous computation and keyboard shortcuts.
- **Connectors** — **Amazon Aurora added as a newly supported database**, including local and global failover, SSL and Hikari pool handling; Databricks OAuth JDBC, views, complex types and `CREATE FUNCTION`; DuckDB binary/varbinary, bit and date-conversion coverage; plus Snowflake, MongoDB, Postgres, ClickHouse, Trino/Athena, Deephaven, Db2/Sybase/Spanner and delegated-Kerberos SQL Server work.
- **Platform modernization & security** — Engine builds moved **JDK 11 → 17** with JDK 21 compatibility, and Pure now builds on **JDK 25** while testing on Java 8 and 17; **SonarQube** was added to the pipelines of Engine, Pure, SDLC and Depot; several CVEs were remediated; **Legend SDLC completed a four-phase re-architecture** (framework-free exception model, project-structure extraction, SDLC core, backend SPI) in July 2026; and Depot replaced hand-rolled dependency resolution with the **Maven Resolver**, with deterministic behaviour.

# Community & Contribution Metrics

Aggregates below cover the **11 Legend repositories with commits to their default branch in the window** — `legend`, `legend-engine`, `legend-studio`, `legend-pure`, `legend-sdlc`, `legend-shared`, `legend-depot`, `pylegend`, `legend-engine-ide-lsp`, `legend-engine-ide-client-vscode` and `legend-pure-next`. Repository "last pushed" dates are not a reliable activity filter for Legend: an automated `MAINTAINERS.md` branch was pushed across ~13 dormant repositories in a 16-minute window on 2026-05-25, which makes 23 of 27 repositories appear active when only 11 are.

**Contributors (GitHub, 12 months)**

- **73 distinct human contributors.** Bots are excluded: `finos-admin` (571 commits, all `maven-release-plugin` version bumps — note it is typed as a `User`, not a `Bot`) and `github-actions[bot]` (278) together account for **849 commits, 28.7% of all commit activity**.
- **23 first-time contributors (~32%)**, contributing 217 commits (10.3% of human commits). This is healthy inflow but shallow — 13 of the 23 made three commits or fewer. *(First-time status is approximate: it means no prior commit in any Legend repository before 2025-07-30, so it under-counts contributors who changed login or email.)*
- **107 quarterly-active contributors** with **69% quarter-over-quarter retention** per LFX Insights.

**Commits (GitHub, 12 months)**

- **2,957 commits** to default branches across the `finos/legend*` repositories, of which **2,108 are human**; `pylegend` contributes a further 115. Busiest repositories: Engine 865, Studio 806, `legend` (documentation) 494, Pure 305, SDLC 176, Depot 144.

**Pull requests (GitHub)**

- **2,754 opened / 2,043 merged** over 12 months; **1,523 opened / 1,092 merged** over 6 months, across the `legend*`-prefixed repositories (PyLegend counted separately, as with commits above).
- **203 currently open** across the eleven actively-developed repositories, with a further 29 stranded in dormant ones. Merged in the last 6 months by repository: Engine 430, Studio 393, Pure 104, SDLC 72, PyLegend 53, Shared 27, Depot 26.
- **Average merge lead time of 2 days**, with **354 of 365 active days**, per LFX Insights.

**Issues (GitHub)**

- **264 currently open**, 176 of them in `legend-studio`. Only **12 issues were opened across all repositories in 12 months** — GitHub Issues is effectively an unused channel for Legend, whose design discussion happens in pull requests and in the component backlogs, so this should be read as a channel-usage fact rather than a decline in engagement. The open count is a long-standing backlog, with the oldest `legend-studio` issues dating to March 2021. **Average issue resolution time 28 days** per LFX Insights.

**Releases**

- **369 releases in 12 months / 216 in the last 6 months**, counted as version tags by tag-commit date. The core Java repositories release via `maven-release-plugin` and publish to Maven Central under `org.finos.legend`; they create git tags but no GitHub Release objects, so the GitHub Releases API reports zero for all of them.
- `legend-studio` releases separately through changesets to npm: **127 publishes** of `@finos/legend-application-studio` in 12 months (56 in the last 6), latest **v28.21.28** on 2026-07-29. This is a different unit and is not folded into the tag counts above.

**Adoption indicators**

- **npm** — roughly **50 published `@finos/legend-*` packages, every one above 20,000 downloads per year**. Leaders over the trailing year: `@finos/legend-graph` **158,121**, `@finos/legend-application-studio` **104,293**, `@finos/legend-query-builder` **79,491**, `@finos/legend-shared` 65,581, `@finos/legend-lego` 59,837. With 127 monorepo publishes a year, a significant share of this volume is CI and mirror traffic; the meaningful signal is the **breadth** of the published surface and the arrival of new entrants such as `@finos/legend-application-marketplace`, `@finos/legend-server-lakehouse` and `@finos/legend-extension-dsl-data-product`.
- **Docker Hub** — approximately **211,000 pulls across the currently-published Legend images**: `legend-studio` 73,296, `legend-engine-server-http-server` 54,799, `legend-query` 22,781, `legend-data-cube` 18,456, `legend-engine-xt-sql-postgres-server` 15,044, `legend-showcase-server` 13,189, plus the Pure IDE and PyLegend images. Legacy and superseded images hold a further ~1.48M historical pulls, which we exclude as they no longer reflect current traction.
- **PyPI** — `pylegend` reached its first stable release, 1.0.0, on 2026-04-24, supporting Python 3.9–3.13.
- **LFX Insights** rates project health **Excellent**, and reports **22,200 monthly search queries** and **2,102 stars / 1,208 forks** at the project level (LFX's cross-repository rollup; the per-repository GitHub sum is ~1,918).

# Challenges & Blockers

- **Organisational — rather than individual — contribution concentration.** These two measures point in opposite directions and both belong in the record. **Individual bus factor is healthy:** no single contributor exceeds **11.5%** of human commits, the top two account for **20.6%** (12 months) / 22.4% (6 months), the top five 42.1% and the top ten 59.0%, spread across 73 contributors — and these ratios are flat between the two windows. **Organisational concentration is the genuine exposure:** Goldman Sachs accounts for **at least 73.7%** of human commits (72.7% over 6 months), and all seven component maintainer teams are effectively 100% Goldman Sachs. That figure is a floor, not a point estimate — 26.2% of human commits come from `users.noreply.github.com` addresses that we have left unattributed rather than guessed at, and positively identified non-Goldman corporate contribution is only ~0.6%. LFX Insights states this as "1 organisation accounts for >51% of contributions" and "8 contributors account for >51% of contributions"; the latter is computed on a different basis from the figures above, which exclude the 849 release-automation commits. Broadening the contributing and maintaining organisation base is the project's single most important health objective.
- **Repository, release and governance hygiene.** Fifteen dormant repositories remain unarchived — the Juju/charm suite has been idle for 19–37 months and three `legend-engine-*` repositories are empty stubs. `legend-config` carries no license file, and `legend-engine-ide-client-vscode` reports NOASSERTION because its Apache-2.0 license sits under `packages/extension/` rather than at the repository root. No core Java repository publishes GitHub Releases, and `legend-studio`'s last git tag is `v13.0.0` (January 2025) against a shipping package version of 13.246.0 — so downstream consumers have no human-readable changelog. The `MAINTAINERS.md` pull requests FINOS opened across the Legend repositories on 2026-05-25 remain unmerged after roughly nine weeks; only `legend-studio` has merged its own. Docker publishing for `legend-sdlc-server` and `legend-depot-server` appears to have stopped in June 2025 despite 110 combined tag releases since, which we are investigating.
- **Dependency backlog.** **59 of 71 open `legend-studio` pull requests are Dependabot bumps**, the oldest untouched since April 2026. Automated updates are arriving faster than they are triaged.
- **Change churn and one alpha component.** 36 revert pull requests merged in the window, 27 of them in Engine (~6.3% of its merged total), including two changes explicitly titled as workarounds for a distributed serializer defect that remains open. Separately, `legend-engine-ide-lsp` still self-describes as prototype/alpha, carries 35 open issues, and has shipped no release in five months despite ongoing commits.

# Roadmap & Goals for Next 6 Months

- **Legend SQL and Relation / TDS 2.0** — continue toward SQL parity as the strategic query path, extending the e2e parity test framework, broadening window and correlated-subquery support, and maturing Relation Function Class Mappings and the Arrow IPC path.
- **Legend AI and MCP** — expand the assistant and MCP server beyond Marketplace into Studio and Query, building on the inline suggestion, chat-agent and analytics work delivered this period.
- **Platform modernization** — complete the Legend SDLC re-architecture beyond the backend SPI phase, finish the PELT metadata rollout across Engine and Pure, complete the JDK 17/21/25 uplift, and mature Data Quality & Reconciliation from new capability to supported feature.
- **`legend-pure-next`** — continue the exploratory track rebuilding Pure around simplicity, nimbleness and self-description.
- **Community and governance remediation**, treated as deliverables rather than aspirations: publish a current roadmap to replace the 2021 wiki page; establish and advertise a discoverable community call; merge the outstanding `MAINTAINERS.md` pull requests across all repositories; archive the dormant repositories; fix the two license-placement gaps; restore Docker publishing for the SDLC and Depot servers; return `legend-sdlc` CI to green; and reduce the Dependabot backlog.
- **Assess lifecycle readiness.** Legend has been Incubating since 2020-10-19. The maintainers will assess readiness for a transition to Graduated against the FINOS criteria during this period, without committing to a timeline ahead of that assessment.

# Additional Information

- **FINOS-hosted shared instance.** FINOS runs a free, as-is shared Legend instance at https://legend.finos.org/studio, primarily for shared modelling by FINOS members and community participants. Models built there are open source and published at https://gitlab.legend.finos.org/. No proprietary models should be built in it.
- **Distribution channels** are broader than GitHub: Maven Central (`org.finos.legend`), npm (`@finos/legend-*`), PyPI (`pylegend`), Docker Hub (`finos/legend-*`) and the VS Code extension. Any assessment of Legend's release cadence from GitHub Releases alone will be misleading.
- **Ecosystem integrations** in the FINOS org include `legend-community-delta` (Spark/Delta Lake extension, published to Maven Central as `org.finos.legend-community:legend-delta`), `legend-integration-juju` (Canonical Juju/Kubernetes operators) and `legend-integration-morphir`. The latter three are currently dormant and are candidates for either renewed investment or archival.
- **Databricks integration** is a long-standing partnership, corroborated this period by substantial Databricks connector work in Engine. PyLegend and Engine are being co-developed, with reverse-PCT integration for the Pandas API landing in the window.
- **Documentation** is actively maintained: the `finos/legend` repository receives automated daily documentation updates generated from Engine, and both Engine and Pure landed substantial hand-written documentation this period, including an EMIT authoring guide and the Data Quality and Reconciliation validation docs.
