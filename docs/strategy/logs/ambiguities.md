# Ambiguities Log

Where the [agentic delivery strategy](../agentic-delivery-strategy.md) failed to resolve a real
decision. One line per entry.

This log is the document's defect list. An agent that could not determine what to do, or that had to
ask, records it here — the failure is in the document, not in the agent. Isolated entries trigger an
amendment; clustered entries mean the diagnosis has moved and the document needs a new phase.

| Date | Decision needed | Why the document did not resolve it | Raised by | Outcome |
|---|---|---|---|---|
| 2026-09-19 | For each of sixteen action classes, may an agent act unsupervised, and should it be given the work? | Not written. The efficiency axis has no measurable inputs — no CI, no agreement rate, no cost data — and the risk axis has no recorded operator positions. See §1.2. | #36 authoring | Open. Interim rule §1.3 applies: recommend-only, no irreversible actions. |
| 2026-09-19 | What does an agent do when a Task's authority is unclear and the operator is unavailable? | §1.3 says stop, but the escalation route is owned by `#15` and does not exist yet. | #36 authoring | Open. Accepted limitation for 0.1: the agent stops and records the block on its issue. |
| 2026-09-19 | Does "independent review" have any meaning with one operator? | `#4` names self-review versus independent review in scope; with no second human the term has no referent. Deferred to `#16`. | #36 authoring | Deferred, with the constraint recorded in §2.3 S12. |
