# Terraform — Interview‑Focused Syllabus (Sub‑module Breakdown)

## Module 0 — Orientation & Setup (Foundations)

### [0.1 — What Terraform is & where it fits](./00-Orientation-and-Setup/0.1-What-Terraform-is-and-where-it-fits.md)

- IaC vs configuration mgmt; declarative DAG, desired state, idempotence
- Providers, resources, data sources, modules; plan vs apply
- State purpose, drift, refresh; CRUD lifecycle
- When to choose TF vs ARM/Bicep/CloudFormation/Pulumi

### [0.2 — Install & CLI tour](./00-Orientation-and-Setup/0.2-Install-and-CLI-tour.md)

- Install paths, verifying version; enabling tab‑completion
- `init`, `fmt`, `validate`, `plan`, `apply`, `destroy`, `show`
- `-chdir`, workdir hygiene; Terraform env vars (`TF_LOG`, `TF_PLUGIN_CACHE_DIR`)
- Exit codes & CI usage; `-detailed-exitcode`

### [0.3 — Different Types of files and dirs](./00-Orientation-and-Setup/0.3-Different-Types-of-files-and-dirs.md)

- All Different types of files and directories in terraform and there use.
- Which files gets commited and which dose not

### [0.4 — Environment patterns](./00-Orientation-and-Setup/0.4-Environment_patterns.md)

- Env folders (`dev/`, `staging/`, `prod/`) structure
- why they are used?
- How to use them?
- Workspaces (multiple states from same config)
- What are the important things that to keep in mind while working with them?

### [0.5 — Root module vs Child Modules](./00-Orientation-and-Setup/0.5-Child_Modules.md)

- Root module vs child modules (encapsulation, reusability, difference, purpose)
- Keeping root module slim and delegating logic to child modules

- Best practices:

  - Keep modules generic (no hardcoding)
  - Pass variables from root
  - Use outputs for clean interfaces

- Module registries (Terraform Registry, private registry) and versioning

### [0.6 — Terraform block](./00-Orientation-and-Setup/0.6-Terraform_block.md)

- `required_version`, pinning best practices; constraints syntax
- `required_providers` with source addresses and versions
- Provider installation mirrors/caching; air‑gapped setup

### [0.7 — Registry overview](./00-Orientation-and-Setup/0.7-Registry_overview.md)

- Providers vs Modules pages; versioning, docs, examples
- Reading “schema” pages; understanding `Computed`, `Optional`, `Required`
- Selecting well‑maintained modules; semver strategy

### [0.8 — CLI config & provider mirrors](./00-Orientation-and-Setup/0.8-CLI_config_provider_mirrors.md)

- `.terraformrc`/`terraform.rc` (`.tfrc`) location
- `provider_installation` with filesystem/network mirrors
- Private registries & credentials; plugin cache policy

## Module 1 — Language Essentials (HCL2)

### [1.1 — Resources & data sources](./01-Language_Essentials/1.1-Resources_and_data_sources.md)

- Arguments vs attributes; computed values and unknowns
- Data source lookups & common pitfalls (ordering, eventual consistency)
- Inter‑resource references; explicit vs implicit dependencies

### [1.2 — Meta‑arguments](./01-Language_Essentials/1.2-Meta_arguments.md)

- `count` vs `for_each`; stable keys; migration patterns
- `depends_on` (when necessary) and hidden dependencies
- `lifecycle` (`create_before_destroy`, `prevent_destroy`, `ignore_changes`)

### [1.3 — Inputs & outputs](./01-Language_Essentials/1.3-Inputs_and_oputs.md)

- `variable` types, defaults, `nullable`; `locals` for DRY
- Output sensitivity; `sensitive = true` effects
- Variable validation blocks (what to check; clear messages)

### [1.4 — Custom conditions & assertions](./01-Language_Essentials/1.4-Custom_conditions_and_assertions.md)

- `precondition`/`postcondition` on resources and outputs
- `check` blocks: shape, where to use (guardrails beyond type checks)
- Designing user‑friendly failure messages

### [1.5 — Expressions & functions](./01-Language_Essentials/1.5-Expressions_and_functions.md)

- Collection types; `for` expressions, splats; `coalesce`, `try`
- `dynamic` blocks to render nested structures
- `templatefile` vs HEREDOC; JSON encoding helpers
- Provider‑defined functions: when they help (validation/encoding)

### [1.6 — Provisioners (last resort) & safer alternatives](./01-Language_Essentials/1.6-Provisioners_and_safer_alternatives.md)

- Why `local-exec`/`remote-exec` are brittle; failure semantics
- Prefer cloud‑init/user data, images, or config mgmt tools
- Event hooks (e.g., pipelines, webhooks) as alternatives

## Module 2 — State & Backends (Team‑Ready)

### [2.1 — State model](./02-State_and_Backends/2.1-State_model.md)

- What’s in state vs not; resources, data, outputs
- Refresh mechanics; unknowns in plan
- State drift and why it happens

### [2.2 — Remote state](./02-State_and_Backends/2.2-Remote_state.md)

- Backends: S3 (+DynamoDB lock), Azure Blob, GCS — pros/cons
- Encryption, locking, IAM/RBAC patterns
- Migrating local→remote with care

### [2.3 — HCP Terraform (Cloud) integration](./02-State_and_Backends/2.3-HCP_Terraform_Cloud_integration.md)

- `cloud` block; CLI login; workspace binding
- Remote ops vs local; saved plans & approvals
- Org/project/workspace concepts

### [2.4 — Consuming remote state](./02-State_and_Backends/2.4-Consuming_Remote_state.md)

- `terraform_remote_state` data source patterns
- Cross‑stack outputs vs provider data sources; trade‑offs
- Versioning & coupling concerns

### [2.5 — State surgery (safely)](./02-State_and_Backends/2.5-State_surgery.md)

- `state mv`, `state rm`, `state pull/push` usage
- Mapping addresses; dry‑runs; backups
- `state replace-provider` for provider source changes

### [2.6 — Backend block deep‑dive](./02-State_and_Backends/2.6-Backend_block_deep‑dive.md)

- Partial config & env var injection
- Workspace key prefixes and naming
- Common migration gotchas (locks, perms)

### [2.7 - Latest Updates for Remote State Management](./02-State_and_Backends/2.7-State_Management.md)

## Module 3 — Modules & Reuse (Scale via Composition)

### 3.1 — Standard module structure

- Inputs/outputs; examples; README with usage
- `versions.tf` discipline; resource addressing stability

### 3.2 — Publishing & versioning

- Public/private registry; publishing flow
- Semver constraints; deprecation notices

### 3.3 — Design patterns

- Thin wrappers vs opinionated modules; composition over inheritance
- Avoid deep nesting; keep variable surfaces small
- Testability & local examples

### 3.4 — Org‑wide “golden” modules

- Version pinning; change logs; migration guides
- Policy of “no breaking changes without major bumps”

## Module 4 — Provider Auth & Multi‑Cloud

### 4.1 — AWS provider auth

- Credential resolution chain; profiles; STS assume‑role
- Least‑privilege IAM; tagging standards

### 4.2 — Azure providers

- AzureRM auth methods (CLI/SPN/workload identity)
- AzAPI for day‑0/preview features; mixing with AzureRM

### 4.3 — GCP provider

- ADC flow; service accounts; WIF (federation)
- Project/folder/org scoping; org policies

### 4.4 — Dynamic provider credentials in pipelines

- OIDC trust, short‑lived creds per run; mapping roles/scopes
- Benefits over static keys; auditability

### 4.5 — Provider aliases & passing providers

- `alias` on provider; `providers` map on modules
- `configuration_aliases` in child modules; multi‑region/multi‑account

## Module 5 — Planning, Execution & Drift

### 5.1 — Plan mastery

- Speculative vs saved plans; human vs JSON output
- `-parallelism` tuning; plan size & readability

### 5.2 — Drift detection

- `-refresh-only` plans; when to schedule
- Triage patterns when cloud truth ≠ state

### 5.3 — Targeting & replacements

- Why `-target` is a last resort (graph skew)
- Prefer `-replace=addr` for safe rebuilds

### 5.4 — Console & debugging

- `terraform console` to inspect types/exprs
- Provider logs, `TF_LOG`; plugin cache

### 5.5 — Plans as data

- `terraform show -json` over plan files
- Feed bots/policies; generate change summaries

## Module 6 — Testing, Linting & Security Scanning

### 6.1 — Native tests

- `terraform test` basics; ephemeral test runs
- Structuring `tests/` and using mocks

### 6.2 — Terratest (Go)

- When to use; infra‑level assertions
- Test env setup/teardown safety

### 6.3 — Static analysis & policy scanning

- TFLint with rulesets; Trivy/Checkov flows
- Scan both files and plan JSON

### 6.4 — Pre‑commit automation

- `pre-commit` hooks for fmt/lint/security
- `terraform-docs` to keep READMEs current

## Module 7 — Policy as Code & Governance

### 7.1 — OPA/Rego with Conftest

- Evaluating plan JSON; common rules (regions, tags, sizes)
- Keeping a shared policy library; CI integration

### 7.2 — Sentinel in HCP Terraform/Enterprise

- Org policy sets; advisory vs mandatory
- Cost estimation data in policy checks

### 7.3 — Drift/Compliance dashboards

- Aggregating test/policy results & cloud controls
- Reporting posture by env/project

### 7.4 — HCP governance levers

- Variable Sets for org‑wide creds/config
- Run Tasks (advisory vs mandatory) to gate runs

### 7.5 — Health assessments

- Enable drift detection & continuous validation
- Scheduling, on‑demand checks, resolving drift

## Module 8 — Secrets & Sensitive Data (Production Hygiene)

### 8.1 — Mark & handle sensitive data

- `sensitive = true`/`nonsensitive()`/`sensitive()`
- Implications for logs/outputs/state

### 8.2 — External secret stores

- Vault, AWS Secrets Manager/SSM, Azure Key Vault, GCP Secret Manager
- Rotations, access patterns, templates

### 8.3 — CI/CD secrets

- OIDC‑based creds; masked logs; least privilege
- No secrets in VCS; per‑env scoping

### 8.4 — Ephemerality & write‑only

- Ephemeral values/resources to avoid persistence
- Write‑only arguments for sensitive inputs on resources

## Module 9 — Refactoring, Imports & Safe Migrations

### 9.1 — Config‑driven import

- `import` blocks; plannable visibility; for_each imports
- Documenting imports and verifying state

### 9.2 — `moved` blocks

- Rename resources/modules without churn
- Address mapping patterns and pitfalls

### 9.3 — `removed` blocks

- Intentional removals; delete vs state‑only removal
- Batch removals with reviewable plans

### 9.4 — State refactors

- `state mv`/`replace-provider` flows
- Workspace considerations in multi‑env setups

## Module 10 — CI/CD & Collaboration at Scale

### 10.1 — GitHub Actions

- `setup-terraform`; PR plan comments; artifacts
- Required checks; `-detailed-exitcode` gates

### 10.2 — Azure DevOps Pipelines

- Marketplace tasks; workload identity to Azure
- Matrix builds across envs/projects

### 10.3 — Jenkins

- Agents/tooling images; credentials handling
- Stages: fmt→lint→plan→policy→apply

### 10.4 — HCP Terraform remote runs

- CLI‑driven runs; remote execution & approvals
- Policy checks and run UI

### 10.5 — HCP Terraform Agents (private/isolated)

- Install agents; agent pools; workspace binding
- Private VCS/private APIs without inbound holes

## Module 11 — Provider Deep Dives (AWS, Azure, GCP)

### 11.1 — AWS patterns

- Multi‑account; assume‑role chains; partitions/regions
- VPC/IAM best practices; mandatory tags via policy

### 11.2 — Azure patterns

- Resource groups, VNets, RBAC scopes
- Using AzAPI to unblock previews; migration to GA

### 11.3 — GCP patterns

- Projects/folders; networks; service accounts
- Org policies; WIF across projects

## Module 12 — Workspaces, Environments & Promotion

### 12.1 — CLI vs HCP workspaces

- Isolation models; naming; secrets segregation
- When to prefer HCP over CLI workspaces

### 12.2 — Env promotion

- Module version pins; promote via PRs
- Plan‑only on PR; apply on protected branches

### 12.3 — Sharing outputs

- `terraform_remote_state` vs data sources
- Breaking dependency cycles; contract outputs

### 12.4 — (Optional) Stacks

- Concepts, components, deployments; `tfstacks` CLI
- Where Stacks fit vs Terragrunt/Terramate

## Module 13 — Performance, Troubleshooting & Reliability

### 13.1 — Graph & parallelism

- Visualize with `terraform graph`; avoid hidden deps
- `parallelism` trade‑offs vs provider throttling

### 13.2 — Provider throttling & retries

- Backoff patterns; resource timeouts; import pacing
- Stabilizing flaky APIs with conditions

### 13.3 — Debugging

- `TF_LOG`/provider logs; `console`; targeted plans
- Drift triage runbooks; minimal repros

### 13.4 — Locks & unlocks

- S3/Dynamo, GCS, Azure Blob lock issues
- `force-unlock` safety and remediation

### 13.5 — Machine‑assisted review

- Parse plan JSON for human summaries
- Highlight destructive changes & cost deltas

## Module 14 — What’s New in Terraform 1.x (Practically Useful)

### 14.1 — 1.5 highlights

- Config‑driven `import` blocks; `check` blocks
- Safer migrations; better plan visibility

### 14.2 — 1.6 highlights

- Native `terraform test`; `.tftest.hcl` basics
- Mocking providers/modules/resources (later 1.7)

### 14.3 — 1.7 highlights

- `removed` blocks for config‑driven state removal
- Enhancements for import; test mocking

### 14.4 — 1.8 highlights

- Provider‑defined functions (extensibility)
- Cross‑resource refactor improvements

### 14.5 — 1.9 highlights

- Stronger input variable validations; cross‑object references
- New templating helpers

### 14.6 — 1.10 highlights

- Ephemeral values/resources; no persistence in state/plan
- Phase‑specific values; safer secret handling

### 14.7 — 1.11 highlights

- Write‑only arguments on managed resources
- Extending ephemerality to resource args

### 14.8 — Stacks (HCP + CLI)

- Stacks overview; when to adopt; CLI (`tfstacks`)

### 14.9 — `taint` deprecation → prefer `-replace`

- Operational shift to reviewable replacements

## Module 15 — Production Security & Compliance

### 15.1 — Org policy baseline

- Mandatory tags; approved regions/services; encryption defaults
- TLS min versions; CMEK/KMS usage; RBAC

### 15.2 — Policy pipelines

- Mix Sentinel/OPA; advisory vs mandatory
- Pre‑apply checks in CI and HCP Terraform

### 15.3 — Sensitive state hygiene

- Remote backends; restricted access; periodic audits
- Drift reports and health assessments

## Module 16 — Capstone Projects (End‑to‑End)

### Capstone A — Multi‑Env AWS Platform (VPC + EKS + RDS)

- Versioned modules; OIDC to AWS; Actions pipeline
- Lint/test/scan gates; S3+Dynamo backend; Run Tasks

### Capstone B — Azure Landing Zone (Hub/Spoke)

- AzureRM + AzAPI; remote state on Blob; ADO pipeline
- OIDC federation; Sentinel/OPA guardrails

### Capstone C — GCP Org + HCP Terraform

- Workspaces per env/project; dynamic creds
- Private registry modules; provider‑defined functions for validation

## (Optional) Module 17 — Ecosystem & Alternatives

### 17.1 — OpenTofu awareness

- What, why some orgs require it; compat considerations

### 17.2 — Orchestration neighbors

- Terragrunt/Terramate vs HCP Stacks; choose by promotion model
