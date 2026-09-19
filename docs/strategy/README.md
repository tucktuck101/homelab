# Strategy

This directory holds the documents that govern **how work is done** in this programme — the rules
agents and the operator follow, and the reasoning those rules rest on.

A strategy here is a decision-making instrument, not a statement of intent. Its test is whether it
resolves a real decision without its author present.

## What Belongs Here

* Rules governing how work is planned, executed, reviewed and accepted
* The diagnosis those rules answer, written as checkable claims
* The tradeoffs each rule makes, and what it forbids

## What Does Not Belong Here

| Content | Belongs in |
|---|---|
| What the programme is for | [`../vision.md`](../vision.md) |
| Evidence gathered while reducing uncertainty | [`../research/`](../research/) |
| A single decision and its consequences | [`../adr/`](../adr/) |
| How the system is built and behaves | [`../architecture/`](../architecture/) |
| The mechanics an agent executes step by step | The execution contract |
| Progress, status or discussion | The issue |

**Strategy versus contract.** The strategy carries the diagnosis and the policy — what is permitted,
what is forbidden, and why. The execution contract carries the operational mechanism an agent runs.
If a statement answers *why is this the rule*, it is strategy. If it answers *what do I type*, it is
contract. This boundary was settled in [`../research/0057-agentic-delivery-evidence-base.md`](../research/0057-agentic-delivery-evidence-base.md).

## Naming

```text
docs/strategy/<topic>-strategy.md
```

Supporting evidence for a strategy lives in `evidence/`, prefixed with the issue that commissioned
it. Operational logs a live strategy accumulates live in `logs/`.

## Status

Every strategy document carries a status in its header.

| Status | Meaning |
|---|---|
| **Drafting** | Being written or revised. Not yet binding. Do not cite it as authority. |
| **Active** | Accepted by the operator, with a version and date recorded. Binding. |
| **Retired** | Closed with a stated reason, and a forward link if superseded. Left in place. |

A retired document is never deleted and never silently edited. An audit trail that is edited to stay
correct is not an audit trail.

## Versioning and Acceptance

A strategy becomes `Active` only when the operator records acceptance — version, date, and what was
accepted — on the Story that commissioned it. Merging a pull request is not acceptance. Nothing
downstream may cite a document that has not been accepted.

## Convention Status

**Provisional.** This convention was established while writing the first strategy document that
needed somewhere to live. The programme's documentation and knowledge strategy (`#53`) will either
adopt it or replace it. Until then, this is the standard.
