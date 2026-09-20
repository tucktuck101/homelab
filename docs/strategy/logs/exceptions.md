# Exceptions Log

Every exception to the [agentic delivery strategy](../agentic-delivery-strategy.md) — **granted or
refused** — is recorded here, one line per entry, before the action it permits.

An unrecorded exception did not happen. It also cannot count towards the three-strikes trigger,
which is the mechanism that converts a recurring exception into an amended rule. See §2.2.

Expiry is mandatory. The default is the Task that requested it; the maximum without explicit
re-approval is one milestone. An expired exception reverts automatically.

Two conditions are required (§1.1). Both are recorded, and a later reader must be able to check
whether each held — an exception whose conditions cannot be re-checked is a log entry, not a
control. "The same exception" for three-strikes purposes means the **same rule and the same effect**,
not the same wording.

| Date | Rule | Action permitted | Condition A | Condition B | Evidence both held | Blast radius if wrong | Decision | Expiry |
|---|---|---|---|---|---|---|---|---|

_No entries. The strategy is binding from 1.0.0 (2026-09-19); no exception has been requested._
