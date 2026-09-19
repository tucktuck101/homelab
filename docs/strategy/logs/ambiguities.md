# Ambiguities Log

Where the [agentic delivery strategy](../agentic-delivery-strategy.md) failed to resolve a real
decision. One line per entry.

This log is the document's defect list. An agent that could not determine what to do, or that had to
ask, records it here — the failure is in the document, not in the agent. Isolated entries trigger an
amendment; clustered entries mean the diagnosis has moved and the document needs a new phase.

| Date | Decision needed | Why the document did not resolve it | Raised by | Outcome |
|---|---|---|---|---|
| 2026-09-19 | For each of sixteen action classes, may an agent act unsupervised, and should it be given the work? | Not written in 0.1. The efficiency axis had no measurable inputs and the risk axis no recorded operator positions. | #36 authoring | **Resolved in 0.2.** Operator supplied positions on merge, host access and small fixes; §1.2 written as a classifier. Four rows remain provisional and nothing is earned by measurement. |
| 2026-09-19 | What does an agent do when a Task's authority is unclear and the operator is unavailable? | §1.2.1 G7 says propose and stop, but the escalation route is owned by `#15` and does not exist yet. | #36 authoring | Open. Accepted limitation: the agent stops and records the block on its issue. |
| 2026-09-19 | Does adopting dependency-update automation give `AC06` a replay (**R**) path? | No such mechanism exists here, so §1.2.1 G4 cannot fire. Whether adopting one would widen `AC06` from **I** to **R** is not decided. | #62 backtest | Open. Adopting one requires a decision record, not an inference from the `AC06` row. |
| 2026-09-19 | Does "independent review" have any meaning with one operator? | `#4` names self-review versus independent review in scope; with no second human the term has no referent. Deferred to `#16`. | #36 authoring | Deferred, with the constraint recorded in §2.3 S12. |
