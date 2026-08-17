# Changelog

All notable changes are recorded here. The project follows explicit milestone and package-version boundaries; deterministic evidence versions are documented separately from real-model studies.

## [0.2.1] — S0 audit-environment security patch

### Security

Updated the development and independent-audit test environment from vulnerable pytest `8.4.2` to pytest `>=9.0.3,<10` after dependency auditing identified [`PYSEC-2026-1845`](https://osv.dev/vulnerability/PYSEC-2026-1845) (`GHSA-6w46-j5rx-g56g`). The advisory affects pytest through `9.0.2` on UNIX because predictable temporary-directory handling may permit a local denial of service or possible privilege gain. The regenerated lock currently resolves pytest `9.1.1`.

The patched environment passed all 122 tests, Ruff formatting/lint, strict Mypy, the example and observe/warn/enforce demo, and the deterministic simulator smoke stage. A subsequent dependency audit reported no known third-party-package vulnerabilities; the local project package itself is not published on PyPI and was therefore skipped by that auditor.

### Scope

No S0 runtime admission, assembly, interception, receipt, trace, replay, scenario, or simulator behavior changed. Version `0.2.0` remains preserved as the original frozen S0 audit candidate; reviewers should use `0.2.1` and its checksum manifest for new audits.

## [0.2.0] — S0 audit candidate

### Added

The S0 milestone introduces verifier-issued provenance bound to exact content bytes, opaque verified segment identities, admission decisions bound to verified trust, deny-by-default source/principal allowlists, attestation lifecycle checks, replay protection within an admission session, and exact one-to-one decision/segment/receipt joins.

Adversarial tests cover raw caller authority claims, forged or altered provenance, expiry and scope failures, revocation, attestation replay, post-verification content substitution, duplicate logical IDs and verified UIDs, missing or surplus decisions, mismatched joins, and duplicate receipt identities.

Repository governance now labels deterministic benchmark outputs as conformance/regression evidence rather than real-model efficacy and freezes S1/provider/real-effect work pending independent S0 review.

### Evidence

The internal release gate reported 122 passing tests, Ruff formatting and lint, strict Mypy, local example/demo execution, and complete deterministic replay of the generated smoke, pilot, and full simulator traces. These facts are documented in `docs/s0_implementation_and_reaudit.md`; they are not a third-party security assessment.

### Deferred

S1 model-facing structural framing and trusted invariant residency, S2 resolved-effect capabilities and authenticated evidence roots, live providers, real effects, and blinded real-model evaluation remain unimplemented or unapproved.

## [0.1.0] — Initial deterministic simulator MVP

Introduced typed context segments, canonical hashing, admission and assembly, deterministic compaction, invariant predicates, simulated effect adapters, pre-effect interception, receipts, deterministic replay, benchmark scenarios, reporting, and CLI workflows. The original simulator-arm separation is conformance plumbing, not causal evidence that context handling changes model behavior.
