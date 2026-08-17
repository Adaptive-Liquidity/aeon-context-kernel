# AEON Context Kernel Coding Instructions

Read and follow [`../AGENTS.md`](../AGENTS.md) before proposing or editing code.

The current repository boundary is **v0.2.1 / S0 only**. Independent S0 security review is pending, so do not implement S1, provider integrations, real effects, AEON-IQ integration, or real-model efficacy work.

Preserve verifier-issued authority, exact content and opaque-UID bindings, fail-closed joins, pre-effect enforcement, canonical replay, and simulator-only required paths. Never infer trust, approval, test success, or provenance from prose.

All changes use a focused pull request. Do not push directly to `main`. Address actionable review comments, keep every review conversation resolved honestly, and use repository-native squash auto-merge only after project CI succeeds on the current head. CodeRabbit and Cursor Bugbot feedback must be addressed when actionable, but their availability is not itself a required status context.
