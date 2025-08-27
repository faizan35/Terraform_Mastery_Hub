# Terraform

## Module 0 — Orientation & Setup (Foundations)

0.1 **What Terraform is & where it fits**: IaC model, declarative graph, providers, modules, state.
0.2 **Install & CLI tour**: `init`, `fmt`, `validate`, `plan`, `apply`, `destroy`, `show`.
0.3 **Project layout**: root module, `*.tf` files, `.terraform/`, dependency lock file `.terraform.lock.hcl`.
0.4 **Terraform block**: `required_version`, `required_providers`, provider installation, mirrors/caching.
0.5 **Registry overview**: providers vs modules; doc navigation.
0.6 **CLI config & provider mirrors**: `.terraformrc`/`terraform.rc` (a.k.a. `.tfrc`), `provider_installation` with filesystem/network mirrors for air-gapped/cached installs.

## Module 1 — Language Essentials (HCL2)

1.1 **Resources & data sources**: arguments, attributes, read-only vs computed; data lookups.
1.2 **Meta-arguments**: `depends_on`, `count`, `for_each`, `lifecycle` (`create_before_destroy`, `prevent_destroy`).
1.3 **Inputs/outputs**: `variable`, `locals`, `output`. Variable validation; 1.9 improvements (cross-object references).
1.4 **Custom conditions**: `precondition`/`postcondition` on resources/outputs; `check` blocks for assertions (added in 1.5).
1.5 **Expressions & functions**: collections, `for` expressions, `dynamic` blocks, `templatefile`, **provider-defined functions (1.8+)** to simplify assertions and custom logic.
**1.6 Provisioners (last resort) & safer alternatives:** when _not_ to use `local-exec`/`remote-exec`, and what to do instead (cloud-init/user-data, config-mgmt, service hooks).

## Module 2 — State & Backends (Team-Ready)

2.1 **State model**: what’s stored; plans vs state; refresh mechanics.
2.2 **Remote state**: S3 (+ DynamoDB locking), AzureRM Blob, GCS; backend configuration; locking & consistency.
2.3 **HCP Terraform (Cloud) integration**: `cloud` block, `terraform login`, workspace linkage.
2.4 **Remote state consumption**: `terraform_remote_state` data source patterns.
2.5 **State surgery (safely)**: `state mv`, `state rm`, `state pull/push`, `state replace-provider`.
2.6 **Backend block deep-dive**: partial configuration, workspace prefixes, migration gotchas.

## Module 3 — Modules & Reuse (Scale via Composition)

3.1 **Standard module structure**: inputs/outputs, versions, docs.
3.2 **Publishing & versioning**: public/private registry, semver, constraints.
3.3 **Design patterns**: thin vs opinionated modules, composition, anti-patterns (deep nesting, tight coupling).
3.4 **Org-wide “golden” modules**: version pinning, changelogs, deprecation policy.

## Module 4 — Provider Auth & Multi-Cloud

4.1 **AWS provider**: credential resolution order; roles; STS; guidance.
4.2 **Azure providers**: AzureRM (CLI/SPN), **AzAPI** for day-0 features.
4.3 **GCP provider**: Application Default Credentials (ADC) best practice.
4.4 **Dynamic provider credentials in pipelines** (OIDC via HCP Terraform) for AWS/Azure/Vault.
4.5 **Provider aliases & passing providers to modules**: `alias`, `provider` meta-arg on resources, `providers` map on module calls, and `configuration_aliases` in child modules.

## Module 5 — Planning, Execution & Drift

5.1 **Plan mastery**: speculative plans; saving plan files; `-parallelism`; `-detailed-exitcode` for CI gates.
5.2 **Drift detection**: `-refresh-only` plans; when/why to run them.
5.3 **Targeting & replacements**: when (rarely) to use `-target`; **prefer `-replace=addr` over the deprecated `taint` workflow**.
5.4 **Console & debugging**: `terraform console` for evals; provider logs; TF_LOG; plugin cache.
5.5 **Plans as data**: `terraform show -json` over a saved plan to drive CI gates, policy checks, and change summaries.

## Module 6 — Testing, Linting & Security Scanning

6.1 **Native tests (1.6+)**: `terraform test`, `tests/`, ephemeral test runs, variables in tests.
6.2 **Terratest (Go)**: integration/E2E tests for modules/envs.
6.3 **Static analysis & policy scanning**: TFLint (rulesets), **Trivy (tfsec engine) / Checkov**; scanning both files and plan JSON.
6.4 **Pre-commit automation**: `pre-commit` framework; `pre-commit-terraform` hooks for `fmt`, TFLint, Trivy/Checkov, and **terraform-docs** to keep READMEs current.

## Module 7 — Policy as Code & Governance

7.1 **OPA/Rego with Conftest**: enforce org rules pre-apply in CI.
7.2 **Sentinel** with HCP Terraform/Terraform Enterprise: cost/region/size guardrails in org workspaces.
7.3 **Drift/Compliance dashboards**: combining tests, policies, and cloud service controls.
7.4 **HCP Terraform governance levers**: **Variable Sets** for org-wide creds/settings; **Run Tasks** (advisory vs mandatory) to gate runs with third-party checks (Snyk, HCP Packer, Infracost, etc.).
**7.5 Health assessments (drift & continuous validation):** enable workspace health to detect configuration **drift** and run **continuous validation**; supports on-demand and scheduled assessments; review results under **Health → Drift**.

## Module 8 — Secrets & Sensitive Data (Production Hygiene)

8.1 **Mark & handle sensitive data**: `sensitive = true`, `sensitive()` function, state implications.
8.2 **External secret stores**: Vault provider, AWS Secrets Manager/SSM, Azure Key Vault, GCP Secret Manager patterns.
8.3 **CI/CD secrets**: OIDC-based ephemeral creds; never hardcode; least privilege.
8.4 **Ephemerality & write-only**: **Ephemeral values/resources (1.10)** to avoid persisting sensitive data; **write-only arguments (1.11)** for securely passing secrets to resources.

## Module 9 — Refactoring, Imports & Safe Migrations

9.1 **Config-driven import** (`import` blocks in 1.5): plan-time visibility; documenting imports.
9.2 **`moved` blocks**: rename resources/modules without churn.
9.3 **`removed` blocks** (1.7): declare intentional removals to prevent recreation.
9.4 **State refactors**: `state mv`, `state replace-provider`, workspaces considerations.

## Module 10 — CI/CD & Collaboration at Scale

10.1 **GitHub Actions**: `hashicorp/setup-terraform`, PR plan comments, artifacted plans, required checks.
10.2 **Azure DevOps Pipelines**: marketplace tasks; OIDC to Azure; integration testing patterns.
10.3 **Jenkins**: pipeline stages, agent tooling, credentials; patterns.
10.4 **HCP Terraform “CLI-driven runs”**: remote execution, policy checks, run UI, workspace controls.
**10.5 HCP Terraform Agents (private/isolated networks):** run plans/applies _inside_ private networks and on-prem by installing self-hosted agents and assigning them to workspace agent pools; useful for vSphere/Nutanix/private VCS without opening inbound access.

## Module 11 — Provider Deep Dives (AWS, Azure, GCP)

11.1 **AWS**: VPC/IAM patterns, multi-account, assume-role, partitions/regions, tagging standards (lint checks).
11.2 **Azure**: resource groups, VNets, RBAC, SPN vs workload identity; when to use AzAPI to unblock preview features.
11.3 **GCP**: projects/folders, networks, service accounts & ADC, org policies.

## Module 12 — Workspaces, Environments & Promotion

12.1 **CLI workspaces vs HCP workspaces**: when to use which; isolation model; naming/versioning.
12.2 **Env promotion**: dev→staging→prod via module version pins, plan-only on PRs, apply on protected branches.
12.3 **Sharing outputs**: `terraform_remote_state` vs data sources trade-offs.
12.4 **(Optional) Stacks**: HCP Terraform **Stacks** concepts and the Stacks CLI (`tfstacks`) to orchestrate multi-component deployments.

## Module 13 — Performance, Troubleshooting & Reliability

13.1 **Graph & parallelism**: avoiding hidden deps, `depends_on` judiciously; visualize with `terraform graph`.
13.2 **Provider throttling & retries**: backoff patterns; `-parallelism`, resource timeouts.
13.3 **Debugging**: TF_LOG, provider logging, `terraform console`, drift triage runbooks.
13.4 **Locks & unlocks**: stuck locks in S3/Dynamo/GCS/Azure Blob; `force-unlock` safety notes.
13.5 **Machine-assisted review**: consuming plan JSON in bots/dashboards (ties back to 5.5).

## Module 14 — “What’s New in Terraform 1.x” (You’ll Use This!)

14.1 **1.5**: Config-driven **`import`** blocks, **`check`** blocks; safer migrations.
14.2 **1.6**: **`terraform test`** (native testing framework).
14.3 **1.7**: **`removed`** blocks; `console -plan` flag.
14.4 **1.8**: **Provider-defined functions** (e.g., richer assertions/validations in expressions).
14.5 **1.9**: Stronger input variable validations (cross-object refs).
14.6 **1.10**: **Ephemeral values/resources** to reduce secret exposure at runtime.
14.7 **1.11**: **Write-only arguments** on managed resources for secrets (extends ephemerality).
14.8 **Stacks (HCP + CLI)**: track Stacks docs/CLI for readiness and organizational fit.
14.9 **`taint` deprecation** in favor of `-replace`.

## Module 15 — Production Security & Compliance

15.1 **Org policy baseline**: mandatory tags, region/governed services, min TLS, encryption defaults.
15.2 **Policy pipelines**: OPA/Rego, Sentinel policy sets, breaking vs advisory.
15.3 **Sensitive state hygiene**: remote backends, restricted access, rotate creds, drift reports.

## Module 16 — Capstone Projects (End-to-End, Real Environments)

**Capstone A — Multi-Env AWS Platform (VPC + EKS + RDS)**

- Golden network, shared services, and app stacks as separate **versioned modules**; promotion via GitHub Actions; OIDC to AWS, **`-detailed-exitcode`** gates; TFLint/Trivy/Checkov; native `terraform test`; S3/DynamoDB backend; drift job with `-refresh-only`; **Run Tasks** (e.g., Infracost/HCP Packer) and **Variable Sets** for org-wide creds.

**Capstone B — Azure Landing Zone (Hub/Spoke) with Workload Identity**

- AzureRM + AzAPI; remote state on Azure Blob; Azure DevOps pipeline with marketplace tasks; OIDC federation; Sentinel/OPA guardrails; import/moved/removed blocks to migrate from manual RGs.

**Capstone C — GCP Org with Projects per Env + HCP Terraform**

- ADC locally; HCP workspaces per env/project; dynamic creds; policies; `terraform_remote_state` to compose shared outputs; **provider-defined functions** for validations; module publishing to private registry.

## (Optional) Module 17 — Ecosystem & Alternatives

17.1 **OpenTofu awareness**: what it is, compatibility, and migration path from Terraform for orgs that require an OSS license.
17.2 **Orchestration neighbors**: when to consider tools like Terragrunt/Terramate vs HCP **Stacks** depending on your promotion model.
