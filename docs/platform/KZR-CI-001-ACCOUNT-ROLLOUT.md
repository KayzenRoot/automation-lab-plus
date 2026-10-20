# KZR-CI-001 | Account-wide professional CI and GEF retirement plan

**Status: CANDIDATE, NOT MERGED, NOT ENABLED IN CONSUMER REPOSITORIES.**
Owner order (2026-10-19): migrate quality workflows to every GitHub repository owned by KayzenRoot, retire active GEF Bootstrap integration without leaving active GEF hooks, maintain source-of-truth evidence, preserve functioning required checks.

## Why staged instead of blindly applying one workflow

Audit enumerated **54** repositories (one empty: BrainBot-2.0-Dev). They include Node, Python, Rust, mixed/multi-root repositories, documentation-only repositories, trading/security-critical services, and repos with existing workflows and branch protections. All consumers need an independently evaluated baseline and replacement check before retiring their GEF entry points; a universal Node job is not sufficient evidence for Python/Rust/Cargo or monorepo quality.

Account is a GitHub **personal user**, not an organization-wide policy engine; a central template alone does not attach itself to all repositories or enforce checks. Each repo requires an explicit caller workflow/PR and read-back verification. This repo is a **candidate public template host**, not yet an approved critical dependency.

## Scoped initial increment

- `.github/workflows/reusable-quality.yml` is a reusable baseline (opt-in with `workflow_call`). No `pull_request_target`, tokens with write scope, production secrets, deploy, publication, billing, remote data or auto-merge.
- Its own `pull_request` trigger tests the host repository candidate. Other repositories are not modified by this PR.
- Gitleaks v3 is pinned to a 40-character SHA, scans Git history according to provider's PR scope; its PASS is not proof the entire legacy history is free of secrets.
- A Node-root lane runs `npm ci --ignore-scripts` and any configured `lint`, `typecheck`, `test:unit`, `build` scripts. Missing manifests/scripts are marked `NOT_APPLICABLE` / `NOT_CONFIGURED`, not represented as full coverage. Project-specific browser, Python, Rust, security, coverage and independent review gates remain required in their respective repos.
- Do not call this workflow from a paid GitHub runner, private-repo billing scope or another project before verifying costs/allowances and appropriate permissions.
- References from future callers must be pinned to a validated **immutable commit SHA after approved merge**, not to `main`.

## Observed GEF footprint requiring impact review

**Active or historically adopted GEF artifacts confirmed by filename/tree evidence**, not proof all are currently executing: 
`hive`, `ugas-v2`, `hive-crypto-trader`, `ml-hunter`, `hive-coder`, `deriv-trader`, `nexlabs-web`, `core`, `iris`, `forge`, `isoryn-engine`, `hive-studio`, `nexlabs-company`, `nexlabs-website`, `zeus`, `nerva-project`, `nex-engine`, `nexlabs-startup`, `goodz-menu`, `poly-hunter`, `iris-studio`, and `spryxel`.

**Specific required caution:** `hive-studio` includes `integrations/gef-bootstrap` as a Git submodule and `.github/workflows/gef-source-validation.yml`; its source-pack validation and integration pin contract must be reconciled, not just delete a YAML. `ml-hunter`, `zeus`, `nerva-project`, `nex-engine`, and `hive-crypto-trader` have similarly named GEF workflows. Other repos have unrelated `GOVERNANCE`/`CHECKPOINT` files that must **not** be mistaken for a GEF Bootstrap installation.

### All 54 KayzenRoot repositories found

- `KayzenRoot/BrainBot`
- `KayzenRoot/BrainBot-2.0-Dev`
- `KayzenRoot/aura-protocol`
- `KayzenRoot/automation-lab-plus`
- `KayzenRoot/beholder_completo`
- `KayzenRoot/brainbot1`
- `KayzenRoot/brainbot2`
- `KayzenRoot/coinblink`
- `KayzenRoot/coinblink-owner-solo-research`
- `KayzenRoot/core`
- `KayzenRoot/deriv-trader`
- `KayzenRoot/fairview`
- `KayzenRoot/forge`
- `KayzenRoot/gef-bootstrap`
- `KayzenRoot/goodz-menu`
- `KayzenRoot/hive`
- `KayzenRoot/hive-coder`
- `KayzenRoot/hive-crypto-trader`
- `KayzenRoot/hive-plan`
- `KayzenRoot/hive-project-v1`
- `KayzenRoot/hive-studio`
- `KayzenRoot/hive-v2`
- `KayzenRoot/hiveforge`
- `KayzenRoot/iris`
- `KayzenRoot/iris-studio`
- `KayzenRoot/isoryn-engine`
- `KayzenRoot/lanchonete-pdv`
- `KayzenRoot/launchbot`
- `KayzenRoot/mktplace`
- `KayzenRoot/ml-hunter`
- `KayzenRoot/nerva-project`
- `KayzenRoot/neryn-world`
- `KayzenRoot/nex-engine`
- `KayzenRoot/nexlabs-company`
- `KayzenRoot/nexlabs-startup`
- `KayzenRoot/nexlabs-tech`
- `KayzenRoot/nexlabs-web`
- `KayzenRoot/nexlabs-website`
- `KayzenRoot/orbi-brain`
- `KayzenRoot/poly-hunter`
- `KayzenRoot/pulse-protocol`
- `KayzenRoot/raven-os`
- `KayzenRoot/solana-microhunter`
- `KayzenRoot/sonoraflow`
- `KayzenRoot/spryxel`
- `KayzenRoot/trade-hunter-mt5`
- `KayzenRoot/uads`
- `KayzenRoot/uads-v2`
- `KayzenRoot/ugas`
- `KayzenRoot/ugas-v2`
- `KayzenRoot/verdant-gateway`
- `KayzenRoot/yoru86`
- `KayzenRoot/zeus`
- `KayzenRoot/zeus-agent`

## Migration gates for every consumer repository

1. Read canonical checkpoint, ADR/Decisions Ledger, Scope, DoD, Architecture, Requirements, current branch protections and CI; capture base SHA and critical file hashes.
2. Classify GEF artifacts as `ACTIVE_RUNTIME_OR_CI`, `ACTIVE_CONFIGURATION`, `HISTORICAL_EVIDENCE`, `NAME_COLLISION`, `UNKNOWN`. Search content and actual GitHub App/settings references, not just filenames.
3. Propose replacement CI with project-specific lint, typecheck, deterministic tests, build, coverage and secret/supply-chain scanners. Keep baseline/required checks, no bypass, no CodeRabbit as a mandatory approval.
4. In **independent repo-specific PRs**, first prove replacement checks green on exact SHA. Only then remove proven GEF activation points (submodules, `.gef` runtime configuration, runner invocations, hooks, workflow calls and direct dependencies), with minimum diff and any necessary canonical ADR/checkpoint updates after approval.
5. Audit final default branch, protected required status checks, repository rulesets and third-party GitHub Apps; remove obsolete settings **only after** replacements are active and verified. Retain useful independent checkpoint/ADR functionality and evidence.
6. Never promise that Git history, historical PRs, commits, forks, cached artifacts or audit trails contain zero mentions. Erasing these requires destructive history rewrite and independent explicit authorization, which is **not** part of this work order. No deleting the `gef-bootstrap` source repository, rewriting refs or removing other users' access.
7. For a HIGH_ASSURANCE financial/trading/Web3/security project, preserve proof obligations and explicit independent review/rollback before any change to protected CI. No upgrades, paid AI credits or SaaS enrollment without verified zero-spend entitlement.
8. Keep each increment `BLOCKED` or `CORRECTION REQUIRED` until actual checks pass, then request owner-authorized merge. No automatic checkpoint promotion.

## Evidence bundle / STOP

Each repository rollout must record base/head SHA, exact changed paths, before/after required checks, runtime/library dependency search, Gitleaks output, test, lint, typecheck, build and coverage results when applicable, open risks, proposed Checkpoint Delta and independent review. **No consumer migration claimed by this candidate PR.** STOP: never merge/deploy/delete repositories or history, activate paid services, overwrite repo rulesets or update canonical checkpoints automatically.


## Correction Delta 1 | Host's missing lockfile

Initial PR HEAD `1b9e05be8f1d0d0d33b80dbcd406676d62db84dc` ran the Gitleaks lane successfully but Node lane failed in `actions/setup-node` because shared templates incorrectly demanded root `package-lock.json` for caching. This host is docs-only. Remove unconditional `cache: npm` and `cache-dependency-path` so docs-only consumers can report `NOT_APPLICABLE` without masking Node build errors. No changes to consumer repositories. Revalidate the exact correction HEAD before any rollout.
