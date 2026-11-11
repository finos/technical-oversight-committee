# High Throughput Compute Grid (HTC-Grid) - Semi-Annual Report [2026 H2]

**Project Maintainers:** [Flamur Gogolli](https://github.com/fgogolli) (Amazon Web Services), [Kirill Bogdanov](https://github.com/kirillsc) (Amazon Web Services), [Clement Rey](https://github.com/clementrey-dev) (Amazon Web Services)

**Repository:** https://github.com/finos/htc-grid

Lifecycle: Incubating · Licence: Apache-2.0 · [Documentation](https://finos.github.io/htc-grid/)

_This is the project's first report in this format. It covers the period since the FINOS contribution (June 2024) to 10 November 2026. Data comes from the GitHub API and the repository history, as of 10 November 2026._

# Project Overview

HTC-Grid is a container-based grid scheduler for AWS. It is a deployable, maintained blueprint for a lightweight, high-throughput scheduler. It runs high volumes of short or long tasks and scales to 30,000+ tasks per second. It suits loosely coupled tasks with different execution times. It is open source, not a supported AWS service.

- An AWS Labs project before its FINOS contribution, which was approved on 7 June 2024 ([finos/community#318](https://github.com/finos/community/issues/318)) and announced on 3 September 2024.
- The default worker backend runs on Amazon EKS. An optional EC2 backend, scaled by FINOS [Open Resource Broker](https://github.com/finos/open-resource-broker) (ORB), is on `main`.

# Current Status

**Key accomplishments**

- HTC-Grid scales an EC2 worker backend through ORB ([#99](https://github.com/finos/htc-grid/pull/99)), alongside the default EKS backend. One `worker_backend` variable selects it (`eks` by default, or `ec2`), and the EKS deployment is unchanged. It is on `main`.
- Clients can submit tasks with dependencies as a directed acyclic graph through client-side DAG support ([#97](https://github.com/finos/htc-grid/pull/97)). Approved; merge pending customer feedback.
- The EC2 backend has an architecture and operations guide, a FAQ, a deployment guide, design decision records and five sequence diagrams.
- ORB's documentation lists HTC-Grid as a grid scheduler that consumes ORB.
- Scan workflows run on every push and pull request: CodeQL, bandit, flake8, cfn-lint, cfn_nag, checkov, trivy, tflint and Terraform checks.

**Major milestones achieved**

- FINOS blueprint, governance and `MAINTAINERS.md` in place ([#82](https://github.com/finos/htc-grid/pull/82), [#98](https://github.com/finos/htc-grid/pull/98)).
- Scan workflows repaired ([#100](https://github.com/finos/htc-grid/pull/100)).

**New features and capabilities delivered**

- EC2 workers with vCPU-based capacity reconciliation ([#99](https://github.com/finos/htc-grid/pull/99))
- Instances are drained only after in-flight tasks finish ([#99](https://github.com/finos/htc-grid/pull/99))
- A warm worker default of one vCPU ([#99](https://github.com/finos/htc-grid/pull/99))
- Multi-grid accounts, with KMS aliases and ECR repositories namespaced per grid ([#99](https://github.com/finos/htc-grid/pull/99))
- Grafana ingress CIDR allow-list ([#99](https://github.com/finos/htc-grid/pull/99))
- Operator submission scripts and an EC2 worker configuration template ([#99](https://github.com/finos/htc-grid/pull/99))
- A paginated, throttling-aware DynamoDB and SQS state client ([#99](https://github.com/finos/htc-grid/pull/99))
- A filtered Grafana dashboard, from an outside contributor ([#92](https://github.com/finos/htc-grid/pull/92))
- Kubernetes components updated to EKS 1.31 ([#89](https://github.com/finos/htc-grid/pull/89))
- Documentation and the workshop stack (Python 3.11) aligned ([#93](https://github.com/finos/htc-grid/pull/93)), deployment scripts pointed at `finos/htc-grid` ([#87](https://github.com/finos/htc-grid/pull/87)), `delete_bucket.py` fixed for Python 3, and `resources.md` updated ([#86](https://github.com/finos/htc-grid/pull/86))

# Community & Contribution Metrics

- Eleven people have contributed since 2021, bots excluded. HTC-Grid has three active maintainers.
- There are 2 open issues and 3 open pull requests, including DAG support ([#97](https://github.com/finos/htc-grid/pull/97)). Users get help through GitHub issues; a Slack channel is being set up.
- The repository has 67 stars, 35 forks and 10 watchers. HTC-Grid is deployed from source, so package and image download figures are not yet available. It is used by numerous tier-one financial services companies.

# Challenges & Blockers

- Community and adoption: use at those companies does not yet show in the issue tracker or contributor base, and all maintainers come from AWS. We would like adopters, contributors and maintainers from member firms.
- Maintainer time is the main resource limit.
- No blockers. Known technical debt: the defaults are due a refresh (EKS 1.31, Lambda Python 3.11, some images on Python 3.8). Each worker pulls one task at a time, which suits larger tasks better than very small ones. Recent changes ship as commits on `main`; versioned releases will resume.

# Roadmap & Goals for Next 6 Months

**Goals.** Keep the blueprint current, grow adoption and attract contributors. All targets are H1 2027.

- Maintenance: move to supported EKS and Python versions.
- Merge client-side DAG support.
- Task batching, so workers pull several small tasks at a time.
- A simple web UI for demos and assessment.
- PyPI packages (client API, utilities and DAG client, agent) and container images built, scanned, signed and published from CI to GHCR.
- Production readiness: unit tests with a coverage gate, required status checks, Dependabot, dependency review, a Scorecard workflow, `SECURITY.md`, an upgrade guide and the OpenSSF Best Practices badge.
- LFX Insights, OpenSSF Scorecard and the Best Practices badge, linked from future reports.
- `good first issue` and `help wanted` labels, GitHub Discussions and the Slack channel.
- Versioned releases, starting with the EC2 backend and DAG support.
- Move the roadmap from our internal backlog to GitHub issues and a project board, which meets the roadmap condition of the FINOS approval.

**Beyond H1 2027.** We are in discussion with external companies, including HMx Labs and Oracle Cloud Infrastructure (OCI), about making HTC-Grid cloud-agnostic and the work needed to get there. It is planned as a future project, run the same way as the ORB integration.

# TOC Support Needed

**Adoption, community and visibility**

- Introductions to member firms and customers with burst-compute workloads, for pilots of HTC-Grid and its EC2 backend and as a route to new adopters, contributors and maintainers.
- Input from member firms on which capabilities matter most.
- Continued exposure to the community, building on our earlier Open Source in Finance Forum (OSFF) talks: OSFF talks and workshops, project booths, and blog posts and videos on Linux Foundation, FINOS and similar channels.
- Exposure at conferences run by sister foundations, such as the High Performance Software Foundation (HPSF).
- A marketing budget for swag, promotional material and presence at FINOS events such as OSFF.

**Cross-project collaboration.** HTC-Grid builds on [Open Resource Broker](https://github.com/finos/open-resource-broker) for its EC2 worker backend.

**Technical guidance.** None needed at this time.

**Lifecycle transition considerations.** No lifecycle change requested.

# Additional Information

- EC2 backend design: [`docs/EC2_BACKEND_ARCHITECTURE.md`](https://github.com/finos/htc-grid/blob/main/docs/EC2_BACKEND_ARCHITECTURE.md).
- `SECURITY.md` is planned, with a private reporting route.
