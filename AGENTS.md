# AEON Context Kernel Agent Instructions

## Canonical state

The canonical repository is `https://github.com/Adaptive-Liquidity/aeon-context-kernel`. The current audit candidate is **v0.2.1**. S0 verifier-issued provenance, exact content binding, opaque segment identity, and one-to-one joins are implemented. An independent third-party S0 security review is still pending.

Do **not** begin S1, provider integration, real effects, AEON-IQ integration, or real-model efficacy work until the independent S0 review has no unresolved Critical or High finding and required fixes are independently retested.

## Required change workflow

Never push directly to protected `main`. Create a focused branch and pull request. Keep changes narrow, document trust/version/evidence impact, and add behavior-focused positive and negative tests.

Repository-native **squash auto-merge** may be queued only after feedback is addressed. It completes only when all of the following gates pass:

| Gate | Requirement |
|---|---|
| Project CI | `Python 3.12 quality and deterministic smoke` succeeds on the current head. |
| Automated review | `CodeRabbit` succeeds. |
| Automated bug review | `Cursor Bugbot` succeeds. |
| Review conversations | Every actionable inline thread is fixed or given a documented disposition and resolved. |
| Branch state | The branch is current with protected `main`. |

Never dismiss a comment, resolve a thread without addressing it, weaken a required check, or bypass branch protection to force a merge. New commits restart the gates.

## Environment and quality gates

Install only from the committed lock:

```bash
uv sync --extra dev --locked
uv run ruff format --check src tests examples
uv run ruff check .
uv run mypy src
uv run pytest
uv run ckernel bench smoke --results-root .ci-results
```

The v0.2.1 lock requires pytest `>=9.0.3` to avoid `PYSEC-2026-1845`; do not reintroduce an affected version.

## Trust and implementation invariants

Authority comes from verifier-issued runtime provenance and policy, never from segment prose or caller claims. Preserve exact content/UID/trust bindings through admission, assembly, compaction, receipts, and replay. Missing, duplicate, surplus, or mismatched bindings must fail closed. Enforcement must complete before any simulated state mutation. Required tests, demos, and benchmark stages remain simulator-only unless a later approved architecture gate explicitly says otherwise.

## Claim boundaries

Describe benchmark outputs as **deterministic conformance/regression evidence**, not real-model efficacy. Replay proves deterministic reconstruction of the simulator decision path; it does not prove model understanding, semantic compliance, artifact authenticity, production security, or prompt-injection immunity. Context-delivery receipts are runtime delivery and policy records, not compliance receipts.

## Evidence and release handling

Preserve historical artifacts and release targets; never rewrite them in place. Generated result trees belong in release assets or explicit audit directories, not ordinary source commits. Every release must bind its source commit, package version, CI state, limitations, and asset checksums. Security fixes must record the advisory, affected/fixed versions, focused tests, full gates, dependency-audit result, and whether runtime behavior changed.

Use the repository’s workflow snapshots under `docs/workflows/` for detailed kernel engineering, benchmark authoring, and reproducibility-audit procedures.
