# Long Ho | DevOps Engineer

## Reusable GitHub Actions

This repository also provides organization-wide reusable workflows under
`.github/workflows/`:

- `python-container.yml` — install, test and build a Python container;
- `node-container.yml` — install, typecheck/build and build a Node container;
- `java-container.yml` — run Maven tests and build a Java container;
- `helm-validate.yml` — lint and render a Helm chart, then validate the
  rendered manifest is non-empty without requiring a cluster connection.

Repositories call a template from a thin workflow in their own repository:

```yaml
jobs:
  verify:
    uses: devsecopslonghn/.github/.github/workflows/python-container.yml@master
    with:
      image_name: example-service
      publish_image: false
    secrets: inherit
```

GHCR publication uses the built-in `github.token`; no external registry
credential is required. A caller can enable it with `publish_image: true`,
`registry: ghcr.io` and a full image name such as
`ghcr.io/devsecopslonghn/example-service`. The template publishes both the
commit SHA and `latest`; pull requests still build without publishing. Pin
callers to a release tag or commit SHA when the template contract is stable.

## Deployment contract

Application workflows publish immutable image tags and update the target Helm
repository. Argo CD is the only component that reconciles Kubernetes; GitHub
Actions does not apply manifests directly.

GHCR packages must be either public for anonymous cluster pulls or private with
an explicitly provisioned Kubernetes `imagePullSecret` backed by a credential
that has package read access. Registry credentials are never committed to a
repository or embedded in workflow logs.

I build CI/CD platforms, deployment automation, and reliability tooling for banking and enterprise systems.

Currently focused on Core Banking, Open Banking, Payment Systems, OpenShift,
GitHub Actions, GitLab CI, Ansible, Helm, and database release automation.

[Website](https://drgdevlab.com) | [LinkedIn](https://www.linkedin.com/in/longhn0710) | [GitHub](https://github.com/devsecopslonghn) | [Email](mailto:longhn0710@gmail.com)

## About

DevOps Engineer based in Ho Chi Minh City, Vietnam, with 3+ years of experience in regulated financial environments.

My work is centered around secure and auditable delivery:

- CI/CD pipeline engineering for multi-environment deployments
- OpenShift and Kubernetes deployment automation
- Reusable GitHub Actions, GitLab CI, and release governance
- Helm-based application delivery for modular upgrades
- Database CI/CD with versioned migrations and rollback planning
- Security scanning integration with SonarQube, Aqua Scanner, Coverity, and BlackDuck
- Monitoring and incident visibility using Grafana, Prometheus, Datadog, Zabbix, and Kibana

## Current Focus

- Managing CI/CD patterns across large banking application portfolios
- Automating deployment workflows for Core Banking, Open Banking, and Payment systems
- Improving release safety through approval gates, audit logs, and rollback strategies
- Building platform workflows that connect Git, Ansible, ITSM, and Microsoft Teams

## Impact Highlights

- Contributed to Temenos T24 R25 go-live delivery in Vietnam through pipeline automation and deployment standardization
- Helped reduce a major banking upgrade window from weeks to days through repeatable CI/CD and Helm-based delivery
- Redesigned JBoss deployment topology for an AML platform to remove avoidable deployment downtime
- Built and maintained automation patterns for WebSphere, JBoss, OpenShift, WSO2 API Manager, and database deployments
- Supported production-grade reliability practices with monitoring, alerting, cleanup automation, and incident response

## Tech Stack

| Area | Tools |
| --- | --- |
| CI/CD | Jenkins, GitLab CI, GitHub Actions, Groovy Pipeline as Code |
| Containers | Docker, Kubernetes, OpenShift OCP, Helm |
| Automation | Ansible, Terraform, Bash, Python |
| Database Delivery | Flyway, SQL versioning, migration and rollback scripts |
| Monitoring | Grafana, Prometheus, Datadog, Zabbix, Kibana |
| Security | SonarQube, Aqua Scanner, Coverity, BlackDuck |
| Artifact Management | Nexus, JFrog Artifactory |
| Cloud | AWS EC2, S3, RDS, ECS, Auto Scaling, Spot Instances |

## Pinned Work

### [drgdevlab_mainpage](https://github.com/devsecopslonghn/drgdevlab_mainpage)

Personal DevOps portfolio built with Astro and Tailwind CSS. It presents my experience, CV, production delivery background, and DevOps project notes.

### [vpnclient](https://github.com/devsecopslonghn/vpnclient)

Personal automation client for VPN connection workflows.

### [exam-database](https://github.com/devsecopslonghn/exam-database)

Simple database design exercise for categories, questions, answer choices, users, and scoring.

### Banking CI/CD Case Studies

Public-safe summaries of real delivery patterns I work with: branch-based release strategy, approval gates, OpenShift rollout design, database migration governance, and monitoring-driven operations.

## Resume

- [View portfolio](https://drgdevlab.com)
- [Download resume](https://drgdevlab.com/resume/Long_Ho_DevOps_Resume.pdf)

## Contact

For DevOps, CI/CD, platform automation, or banking delivery discussions:

- Email: [longhn0710@gmail.com](mailto:longhn0710@gmail.com)
- LinkedIn: [linkedin.com/in/longhn0710](https://www.linkedin.com/in/longhn0710)
