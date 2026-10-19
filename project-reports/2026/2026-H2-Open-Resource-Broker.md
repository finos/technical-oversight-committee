# Open Resource Broker - Semi-Annual Report [2026 H2]

**Project Maintainers:** [Flamur Gogolli](https://github.com/fgogolli) (Amazon Web Services), [Kirill Bogdanov](https://github.com/kirillsc) (Amazon Web Services), [Cyriaque Millot](https://github.com/cyriaquem) (Morgan Stanley)

**Repository:** https://github.com/finos/open-resource-broker

Lifecycle: Incubating · Licence: Apache-2.0 · [Documentation](https://finos.github.io/open-resource-broker) · [Roadmap project](https://github.com/orgs/finos/projects/144) (FINOS org members) · [LFX Insights](https://insights.linuxfoundation.org/project/open-hostfactory-plugin) · [OpenSSF Scorecard](https://scorecard.dev/viewer/?uri=github.com/finos/open-resource-broker) · [OpenSSF Best Practices](https://www.bestpractices.dev/projects/13611)

_This is the project's first report. It covers 1 January to 7 October 2026. Data comes from the GitHub API, LFX Insights, the OpenSSF Scorecard API and the package registries, as of 7 October 2026._

# Project Overview

Open Resource Broker (ORB) is a unified API for orchestrating and provisioning compute capacity. Define what you need in a template, then request it, track it and return it through a CLI, a REST API, an MCP server or native SDKs for Python, Go, TypeScript, Java, Kotlin and .NET, whichever provider supplies the capacity.

ORB currently supports four providers, AWS, Microsoft Azure, Google Cloud and Kubernetes, and three schedulers: its own default scheduler, IBM Spectrum Symphony Host Factory and Slurm Workload Manager.

The project began in February 2025 as Morgan Stanley's Kubernetes provider for IBM Spectrum Symphony Host Factory, with AWS building an AWS provider in `awslabs`. The TOC accepted it as an Incubating project on 10 September 2025 under the proposal name `open-hostfactory-plugin` ([TOC #227](https://github.com/finos/technical-oversight-committee/pull/227)). The project was renamed Open Resource Broker in December 2025, when the original repository moved into the FINOS organisation. That repository is now called `finos/open-resource-broker-formation`. FINOS announced the contribution on 14 April 2026. In early June 2026 the AWS codebase moved from `awslabs` into the FINOS organisation, and on 4 June it was combined with the original FINOS repository. The Kubernetes code was merged in with its full commit history ([#229](https://github.com/finos/open-resource-broker/pull/229)), and the repository was aligned with FINOS requirements, including a NOTICE file shared between AWS, Morgan Stanley and FINOS ([#231](https://github.com/finos/open-resource-broker/pull/231)). The Kubernetes provider now ships as the `k8s_legacy` module ([#274](https://github.com/finos/open-resource-broker/pull/274)).

# Current Status

**Key accomplishments**

ORB now gives one API for requesting compute capacity across four providers and three schedulers. The project made 22 releases this year, from `v1.0.0` (6 January) to `v1.8.5` (24 July), and merged 283 pull requests, 81 of them Dependabot updates.

- **Providers.** ORB supports four providers, listed here in the order they were added. AWS came first and covers EC2 RunInstances, EC2 Fleet, Spot Fleet, Auto Scaling groups and AWS Lambda MicroVMs. The MicroVM handler ([#317](https://github.com/finos/open-resource-broker/pull/317)) was added shortly after AWS launched that API. The native Kubernetes provider ([#275](https://github.com/finos/open-resource-broker/pull/275), [#296](https://github.com/finos/open-resource-broker/pull/296), [#326](https://github.com/finos/open-resource-broker/pull/326)) runs Pod, Deployment, StatefulSet and Job workloads. It also has a documented extension route for custom resources defined by CRDs, with a worked example for Kubeflow MPIJob, so future integrations can add their own handlers. The earlier Kubernetes Host Factory code was merged with its full history ([#229](https://github.com/finos/open-resource-broker/pull/229)). Microsoft Azure ([#258](https://github.com/finos/open-resource-broker/pull/258)) supports VM Scale Sets, single VMs and CycleCloud cluster nodes, and Google Cloud ([#257](https://github.com/finos/open-resource-broker/pull/257)) supports managed instance groups and single Compute Engine VMs, with spot capacity on both. Azure and Google Cloud ship in 1.9. Contributors outside the maintainer group wrote the Microsoft Azure, Google Cloud and Slurm support, and the Oracle Cloud Infrastructure provider ([#234](https://github.com/finos/open-resource-broker/pull/234)) is in progress.
- **Schedulers.** The default scheduler and IBM Spectrum Symphony Host Factory are joined by Slurm Workload Manager ([#246](https://github.com/finos/open-resource-broker/pull/246)), which ships in 1.9.
- **SDKs.** The Python package is the core SDK. The Go, TypeScript, Java, Kotlin and C#/.NET SDKs are generated from its OpenAPI specification and talk to ORB over HTTP, and the Go SDK can also run a local ORB process and connect over a Unix socket ([#319](https://github.com/finos/open-resource-broker/pull/319), 20 July; [#193](https://github.com/finos/open-resource-broker/pull/193)).
- **ORB UI.** An optional web interface, installed with `orb-py[ui]` and served on the same port as the API, lets users browse templates, requests and machines, request and return capacity, and watch requests update live ([#284](https://github.com/finos/open-resource-broker/pull/284), [#310](https://github.com/finos/open-resource-broker/pull/310), [#348](https://github.com/finos/open-resource-broker/pull/348)). The `orb requests watch` command gives the same live view in the terminal ([#205](https://github.com/finos/open-resource-broker/pull/205), [#210](https://github.com/finos/open-resource-broker/pull/210)).
- **Quick start.** `orb init` creates a working configuration, interactively or with flags for scripted setup, and `orb templates generate` writes example templates for a provider, or for every configured provider with `--all-providers` ([#123](https://github.com/finos/open-resource-broker/pull/123), `v1.2.0`, 28 January). `orb init` was extended with Kubernetes discovery ([#275](https://github.com/finos/open-resource-broker/pull/275)), and `orb templates generate` with Slurm partition templates ([#394](https://github.com/finos/open-resource-broker/pull/394)).
- **Integrations.** Other FINOS projects now build on ORB to provision compute capacity. [OpenGRIS Scaler](https://github.com/finos/opengris-scaler) uses ORB to provision AWS EC2 workers through its [ORB worker manager](https://github.com/finos/opengris-scaler/blob/main/docs/source/tutorials/worker_managers/orb_aws_ec2/index.rst), and [HTC-Grid](https://github.com/finos/htc-grid) uses ORB to scale its [EC2 worker backend](https://github.com/finos/htc-grid/blob/main/docs/EC2_BACKEND_ARCHITECTURE.md), beside its default EKS backend. ORB is therefore already the capacity layer for two other FINOS compute projects.

**Engineering and security**

- `main` requires approvals and 15 status checks, including architecture ratchet tests, pyright and Ruff with security rules ([#543](https://github.com/finos/open-resource-broker/pull/543)).
- Container images for linux/amd64 and linux/arm64 across Python 3.10 to 3.14 are signed with cosign and carry SLSA provenance and SBOM attestations ([#311](https://github.com/finos/open-resource-broker/pull/311)). Releases from `v1.8.3` carry in-toto attestations.
- 1,002 code-scanning alerts were resolved in 2026: 461 from Trivy, 456 from CodeQL, 83 from OpenSSF Scorecard and 2 from Hadolint. The full set of scanners is CodeQL for Python and GitHub Actions (security and code quality queries), GitHub code quality findings, Semgrep, Trivy (filesystem and container image), Hadolint, TruffleHog secret scanning, pip-audit, Dependency Review and OpenSSF Scorecard. Ruff, including its security rules, and pyright check the code itself.
- FINOS licence gates run on every pull request, and every third-party GitHub Action is pinned to a commit SHA.
- SDK contract and parity tests run against the wheel built from each pull request, and a drift guard fails the build if the committed OpenAPI specification differs from the server's export.
- The suite grew from 1,944 tests in 161 files to 16,330 tests in 984 files. Coverage grew from 58% to 85% (first Codecov report in July to now), with an 80% gate on merges ([#320](https://github.com/finos/open-resource-broker/pull/320), [#396](https://github.com/finos/open-resource-broker/pull/396)).
- The OpenSSF Scorecard result is 8.1, the Best Practices badge has been at passing since 14 July, and the LFX Insights health score is 83/100.

**Major milestones achieved**

- 14 April: FINOS announced the contribution of Open Resource Broker ([announcement](https://groups.google.com/a/finos.org/g/announce/c/UMzWbQcges8)).
- 4 June: the AWS codebase and the original FINOS repository were combined in `finos/open-resource-broker` and aligned with FINOS requirements ([#231](https://github.com/finos/open-resource-broker/pull/231)).
- 14 July: the native Kubernetes provider ([#275](https://github.com/finos/open-resource-broker/pull/275), merged 7 July, and [#296](https://github.com/finos/open-resource-broker/pull/296), merged 13 July) first shipped in `v1.8.0`.
- 15 to 24 July: the signed, attested release pipeline went live, and the SDK packages were published to npm and NuGet through trusted publishing ([#331](https://github.com/finos/open-resource-broker/pull/331), [#333](https://github.com/finos/open-resource-broker/pull/333)). `orb-py` has been on PyPI since 21 January.
- 23 September: the Microsoft Azure provider was merged ([#258](https://github.com/finos/open-resource-broker/pull/258)).
- 2 October: the Google Cloud provider was merged ([#257](https://github.com/finos/open-resource-broker/pull/257)).
- 5 October: the Slurm Workload Manager scheduler was merged ([#246](https://github.com/finos/open-resource-broker/pull/246)).
- 5 October: project planning moved to public GitHub Issues and the roadmap project.

**New features or capabilities delivered**

- Native Kubernetes workload types: provision Pod, Deployment, StatefulSet and Job workloads as machines ([#275](https://github.com/finos/open-resource-broker/pull/275), [#296](https://github.com/finos/open-resource-broker/pull/296), [#326](https://github.com/finos/open-resource-broker/pull/326))
- Provider plugin model: add a provider as one package with an entry point and typed extension points ([#253](https://github.com/finos/open-resource-broker/pull/253), [#285](https://github.com/finos/open-resource-broker/pull/285), [#314](https://github.com/finos/open-resource-broker/pull/314))
- Shared operation catalogue: CLI, REST, SDK and MCP return identical bodies from one declaration per operation ([#339](https://github.com/finos/open-resource-broker/pull/339)) (ships in 1.9)
- Unified MCP server: one MCP server on the official SDK, with tools derived from the catalogue ([#345](https://github.com/finos/open-resource-broker/pull/345)) (ships in 1.9)
- Request watch view: `orb requests watch` shows live request progress in the terminal ([#205](https://github.com/finos/open-resource-broker/pull/205), [#210](https://github.com/finos/open-resource-broker/pull/210))
- Blocking wait mode: `--wait` on the CLI and SDKs returns once a request settles ([#348](https://github.com/finos/open-resource-broker/pull/348))
- Request fulfilment state machine: partial and failed requests record why they ended ([#332](https://github.com/finos/open-resource-broker/pull/332))
- Capacity semantics: weighted EC2 Fleet, Spot Fleet and Auto Scaling group requests report fulfilled capacity correctly ([#253](https://github.com/finos/open-resource-broker/pull/253))
- OpenTelemetry metrics and traces: one stack for all providers, with Prometheus scraping and OTLP export ([#291](https://github.com/finos/open-resource-broker/pull/291))
- Health probes: `/livez` and `/readyz` separate process liveness from dependency readiness ([#350](https://github.com/finos/open-resource-broker/pull/350)) (ships in 1.9)
- AWS Lambda MicroVM handler: provision isolated Firecracker-based sandboxes, contributed from outside the maintainer group ([#317](https://github.com/finos/open-resource-broker/pull/317))
- AWS resource discovery: list VPCs, subnets and security groups through the API to help build templates ([#349](https://github.com/finos/open-resource-broker/pull/349)) (ships in 1.9)
- Go SDK Unix-socket mode: the Go client manages an ORB subprocess over a Unix socket ([#193](https://github.com/finos/open-resource-broker/pull/193))
- Slurm partition-aware templates: generate one template per partition from `slurm.conf`, with hostlist expansion ([#394](https://github.com/finos/open-resource-broker/pull/394)) (ships in 1.9)
- Fail-closed authentication: anonymous callers are viewers, and roles are enforced on every route ([#276](https://github.com/finos/open-resource-broker/pull/276), [#302](https://github.com/finos/open-resource-broker/pull/302))
- Token revocation: revoked tokens are denied, with fingerprints instead of raw tokens in storage ([#408](https://github.com/finos/open-resource-broker/pull/408)) (ships in 1.9)
- SQL storage hardening: Alembic migrations and optimistic concurrency control ([#241](https://github.com/finos/open-resource-broker/pull/241), [#276](https://github.com/finos/open-resource-broker/pull/276))
- JSON storage locking: cross-process file locking prevents lost updates ([#122](https://github.com/finos/open-resource-broker/pull/122))

# Community & Contribution Metrics

**Contributors.** Fifteen people have contributed to ORB since February 2025, counting the history of the Kubernetes provider. Bots are excluded, and each name links to the person's GitHub profile.

- The maintainers continue as [Flamur Gogolli](https://github.com/fgogolli), [Kirill Bogdanov](https://github.com/kirillsc) and [Cyriaque Millot](https://github.com/cyriaquem).
- Active in 2026: [Alex Kimber](https://github.com/canonicalname) reviews and contributes code.
- New in 2026: [Ike Milian Lewis](https://github.com/IkeM-L) added the Azure and Google Cloud providers, and [Camille Roussel](https://github.com/wettowelreactor) added the Slurm scheduler. [Nicholas Cusato](https://github.com/ncusato) proposed the Oracle Cloud Infrastructure (OCI) provider, [#234](https://github.com/finos/open-resource-broker/pull/234), which is in progress. [Parth Pandit](https://github.com/parth-pandit) made a web UI proposal ([#254](https://github.com/finos/open-resource-broker/pull/254)) that was not merged, and [George L.](https://github.com/magniloquency) filed a bug report ([#185](https://github.com/finos/open-resource-broker/issues/185)).
- The Kubernetes provider's 2025 contributors, through commits, reviews or design comments in the project history, are [Brian Ingenito](https://github.com/bingenito), [Zaid Naji](https://github.com/otonik), [Mark Scannell](https://github.com/mescanne), [`jsiembida`](https://github.com/jsiembida), [`andreikeis`](https://github.com/andreikeis) and [`sujeetkp`](https://github.com/sujeetkp). Cyriaque Millot, listed above, made most of the commits.

**Open PRs.** There are 13 open pull requests. Six are Dependabot updates, six come from the maintainers, and one is the OCI provider ([#234](https://github.com/finos/open-resource-broker/pull/234)).

**Open issues.** There are 123 open issues. They form the public backlog, which the roadmap project organises by milestone.

**Downloads and adoption indicators.**

- The repository has 18 stars and 12 forks.
- The `orb-py` package on PyPI recorded 52,039 downloads between 21 January and 6 October, or 40,882 when mirrors and requests with no user agent are excluded ([ClickHouse PyPI dataset](https://clickpy.clickhouse.com/dashboard/orb-py)). June and July include a large automated pipeline that installs a pinned version. In a typical month the figure is between 1,000 and 4,000.
- The container image on GHCR shows 3,240 pulls since 4 June, which is an upper bound on real use because the project's own CI pulls the image to scan and verify it, and the release tags account for only a few hundred of them.
- The npm package `@finos/open-resource-broker` has had 375 downloads since 23 July, and the NuGet package `FINOS.OpenResourceBroker` has had 371. Release assets on GitHub were downloaded 268 times in 2026.

# Challenges & Blockers

**Technical challenges.** No technical problems are blocking progress at present. The codebase, CI and release process are in good shape, as Current Status shows.

**Resource constraints.** The main limit on the project is maintainer time and community support. Three maintainers and one regular outside reviewer handle most reviews and releases, so larger contributions take longer to review.

**Community or adoption barriers.** The main barrier is reaching new users and organisations. ORB already runs in several organisations, and we want to build a wider community of users and contributors around that use.

# Roadmap & Goals for Next 6 Months

**Goals.** Our main goals are to grow adoption and to increase the number of active contributors. We want to plan future work backwards from what users, member firms and the industry need. The backlog is healthy, but we would welcome outside input on which direction to take next.

**Upcoming milestones.**

- Version 1.9 is planned for this week. It brings the current work across the existing schedulers, including Slurm, and the fixes merged since `v1.8.5`: authentication hardening, provider fixes and the MCP server upgrade to the 2.x SDK ([#534](https://github.com/finos/open-resource-broker/pull/534), in review).
- Version 1.10 is planned for the following week, once the OCI provider, which is in progress, lands.
- After that, we plan to settle into a regular release cadence.

**Planned features and releases.** These are intentions rather than commitments, and the order of the work will follow the input we receive.

- Authentication and authorisation hardening ([#410](https://github.com/finos/open-resource-broker/issues/410)) and an observability pipeline ([#465](https://github.com/finos/open-resource-broker/issues/465)) are planned for Q4 2026.
- Provider and scheduler decoupling ([#495](https://github.com/finos/open-resource-broker/issues/495)) is planned for Q4 2026 to Q1 2027.
- Deployment guidance and tooling ([#496](https://github.com/finos/open-resource-broker/issues/496)) are planned for Q1 2027.
- Research on placing capacity across providers, covering load balancing, fallback and price-aware provisioning ([#432](https://github.com/finos/open-resource-broker/issues/432)), is planned for Q1 2027.
- An Apache Spark cluster-manager plugin ([#478](https://github.com/finos/open-resource-broker/issues/478)) is planned for Q1 to Q2 2027.
- Daemon mode with pluggable demand sources ([#479](https://github.com/finos/open-resource-broker/issues/479)) is planned for Q2 2027.

# TOC Support Needed

The TOC can help us reach these goals in the ways below. The first group holds our main requests.

**Adoption, community and visibility**

- Help reaching firms and projects that need dynamic compute capacity.
- Help growing the community, including new maintainers and reviewers.
- More visibility, such as a FINOS blog post and newsletter or social media coverage.
- Input from member firms on which providers, schedulers and integrations matter most to them.

**Cross-project collaboration.** ORB already integrates with FINOS [HTC-Grid](https://github.com/finos/htc-grid) and [OpenGRIS Scaler](https://github.com/finos/opengris-scaler). We would like to build similar integrations with other projects that need compute capacity on demand, and we welcome issues or discussions from any project that is interested in one.

**Technical guidance.** We do not need technical guidance from the TOC at present.

**Lifecycle transition considerations.** ORB is an Incubating project, and we are not requesting a change of lifecycle stage this period.

# Additional Information

- `SECURITY.md` sets out private reporting through GitHub Security Advisories and the FINOS disclosure channel. Fixes are backported to the latest minor release line.
- LFX Insights lists the project under its pre-FINOS slug, `open-hostfactory-plugin`, taken from the project's 2025 package name.
