# Changelog

All notable changes are recorded here. The project follows explicit milestone and package-version boundaries; deterministic evidence versions are documented separately from real-model studies.

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
