# Acceptance Record — Agentic Delivery Strategy 1.0.0

Required by [#36](https://github.com/tucktuck101/homelab/issues/36) acceptance criterion 4 and
[#66](https://github.com/tucktuck101/homelab/issues/66).

| | |
|---|---|
| **Document** | [`../agentic-delivery-strategy.md`](../agentic-delivery-strategy.md) |
| **Version accepted** | **1.0.0** (from `0.8.0-draft` at commit `b354248`) |
| **Date** | 2026-09-19 |
| **Accepted by** | @tucktuck101, the operator |
| **Effect** | The document is `Active` and binding. Downstream work may cite it. |

## The instruction

Given in a live working session on 2026-09-19, quoted verbatim and untidied per §1.1:

> im saying this is good enough for v1 of the strat and accept it

**Agent-exercised.** This record was written by an AI agent under the strategy's own §1.1
provenance rule, on the operator's live instruction. The agent did not decide the acceptance and
has no authority to; it recorded a decision the operator made. Per `AC14b` this is the `G7` route —
recording a change the operator has already adopted and instructed.

## What was accepted

The document as it stood, **including its stated gaps**, which are not defects overlooked at
acceptance but positions taken deliberately:

- **Nothing in the autonomy boundary has been earned by measurement.** The agreement rate that
  would permit promoting any row does not exist. `#66` owns it.
- **Four rows are provisional** — `AC06` dependency changes, `AC07` CI changes, `AC10` deployment,
  `AC16` spending — resting on no precedent in this repository.
- **No rule is mechanically enforced.** `master` has no branch protection; there is no CI, no test
  suite and no linter. The document describes cooperation, not containment. `#42` and `#47` own
  the mechanisms.
- **The `I`-level instruction record is written by the agent it authorises**, and nothing verifies
  it. Named in §1.1 as the weakest joint and load-bearing. The fix is a distinct agent identity,
  owed to `#42`.
- **The replay level is unreachable.** Runbooks and a mechanism registry are deferred out of this
  milestone by operator decision.
- **Eight of sixteen action classes have never been exercised here**, and the classifier has never
  been tested against a case where it *permits* something that turns out to be wrong.

## Provenance of the document itself

Seven rounds of independent adversarial review by two models on different families — Fable and
OpenAI Codex — fourteen reviews in total, each conducted without sight of the other's output.
Rounds one to five each returned at least one blocker; four of those were defects introduced by the
previous round's fixes. Rounds six and seven returned accept-as-is from both reviewers.

Two corrections were made *downward* during that process: the backtest's divergence count fell from
four to three, and five actions were reclassified from clean reproductions to indeterminate because
they predate the Task model.

## Review

**First review: 2026-10-17**, or on the first agent-executed Story touching an action class other
than documentation, whichever comes first.

The update triggers are in the document's [Refine](../agentic-delivery-strategy.md#refine) section.
Amendment is expected and cheap; a new phase is expensive and rare; the distinction is which of
them a trigger calls for.
