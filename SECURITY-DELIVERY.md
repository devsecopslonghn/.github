# Secure delivery contract

Use full commit SHAs for reusable workflows and third-party actions. Automated dependency PRs update the pins. Verification jobs have read-only GITHUB_TOKEN; registry publication is a separate dependent job. Images are named by repository and commit SHA and expose a digest output; GitOps changes must reference that digest. Do not deploy `latest`.

Container builds attach SBOM and provenance using Buildx. Source security scans use Gitleaks with full redaction, and Trivy for dependencies and IaC. A source scan is not a substitute for scanning the final image. Callers must opt into the reusable source-security workflow; merely adding it here does not enable it in every repository.

GitOps automation should create a PR using a GitHub App installation token scoped to the chart repository (contents and pull requests write). App registration, installation and private-key injection remain outside Git; no App credential has been provisioned by this change. Existing GITOPS_TOKEN callers must remain explicitly tracked until migration is proven. Do not substitute a new unbounded PAT.

Keyless image signing requires caller id-token permissions, an issuer/identity verification policy and a staged admission rollout. Signing/admission enforcement is not enabled by this commit. Package cleanup defaults to a dry run and must retain deployed digests and attestations before any approved deletion.

Branch convention: `fix/`, `feat/`, `hardening/`, `migration/`; review through PRs, conventional commit messages, immutable release tags and commit digests. A GitHub plan restriction on private repository protection is an unresolved platform dependency, never a reason to make internal repositories public.
