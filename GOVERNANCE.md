# Repository Governance

## Maintainer authority

The repository owner is the final maintainer for merges, releases, security embargoes, and milestone transitions. Maintainers may delegate review, but no reviewer may waive the security and evidence gates documented here.

## Branch and merge policy

`main` is the canonical branch. Changes should arrive through pull requests with passing CI. Direct force pushes and branch deletion should be blocked. At least one approving review should be required when more than one maintainer or reviewer is available; an author must not treat their own review as an independent security review.

## Milestone gates

| Gate | Scope | Required evidence before advancing |
|---|---|---|
| **S0** | Verifier-issued provenance, exact content binding, opaque identity, and exact joins | Behavior tests, source gates, deterministic conformance evidence, and an independent S0 security review with no unresolved Critical/High finding. |
| **S1** | Structurally unambiguous model-facing envelope, trusted invariant registry, and compaction integrity | Separate change plan, adversarial tests, fresh deterministic evidence, and independent review. |
| **S2** | Canonical resolved-effect capabilities, single-use approvals, redaction, and authenticated evidence roots | Separate threat model, simulator-first implementation, adversarial race/rebinding tests, and independent review before real effects. |
| **Model study** | Blinded, held-out real-model evaluation | Frozen architecture gates, preregistered metrics and non-inferiority margin, fixed model revisions, and a signed study manifest. |

No milestone is considered complete merely because its code exists. The associated evidence and review gate must also pass.

## Evidence classes

The repository uses precise evidence labels:

| Label | Meaning |
|---|---|
| Unit/integration test evidence | A behavior passed under the tested implementation and fixture. |
| Deterministic conformance evidence | Simulator artifacts can be structurally checked and logically replayed under the stated versions. |
| Independent security-review evidence | A separate reviewer attempted specified attacks and reported findings against a frozen source identity. |
| Real-model experimental evidence | A bounded study measured proposals or task outcomes under fixed models and a preregistered protocol. |

These labels are not interchangeable. Simulator survival curves are not efficacy curves, and replay is not evidence that a model understood or followed instructions.

## Release policy

Every release must identify the source commit, package version, milestone, CI status, known limitations, and any evidence archive checksum. A release containing a logical decision, schema, trace, receipt, scenario, adapter, or report-contract change must explain the version/hash impact.

Security-sensitive releases must not claim closure until the relevant independent retest is attached or linked. Generated result directories should be distributed as release assets or reproducible artifacts rather than committed to normal source history.

## Change control during audit

When a version is under independent review, its source archive and checksum are frozen. Remediation occurs on a new branch and produces a new commit or release candidate. The original audit target remains available for comparison; it is not rewritten in place.
