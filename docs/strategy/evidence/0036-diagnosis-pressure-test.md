# Diagnosis Pressure-Test

Testing the [Diagnose](../agentic-delivery-strategy.md#diagnose) section of the agentic delivery
strategy against what has actually happened in this programme. Commissioned by
[#60](https://github.com/tucktuck101/homelab/issues/60).

The question is not *is the diagnosis agreeable* but *does it explain the decisions and actions
already taken*. A claim that explains nothing is decoration. A decision the diagnosis cannot explain
is a gap.

Corpus: [`0036-recorded-decisions.md`](0036-recorded-decisions.md).

---

## Part 1 — The nine programme decisions

| Decision | Claims that explain it | Explained |
|---|---|---|
| D1 public repository | D-03 | **Fully** |
| D2 no licence | D-17 (after amendment) | **Fully, after amendment.** Before the test, nothing in the diagnosis predicted a decision that was never taken |
| D3 M1 dated, M0 not | D-06, D-11 | **Partly.** The diagnosis explains why M0 is open-ended; it does not explain why M1 carries a date at all |
| D4 M0 gates M1 | D-02, D-11 | **Fully** |
| D5 strategy before implementation | D-11, D-01 | **Fully** |
| D6 backlog upfront, Tasks not | D-06, D-09 | **Fully** |
| D7 Spikes scheduled on contact with uncertainty | D-06, D-09 | **Fully** |
| D8 Tasks authored at pickup | D-06, D-09 | **Fully** |
| D9 Spikes created at pickup | D-06, D-09 | **Fully** |

## Part 2 — The nine agent-executed actions

| Action | Claims that explain it | Explained |
|---|---|---|
| A-01 authored the backlog | D-05 | **Fully** |
| A-02 raised Spike #57 | D-06, D-09 | **Fully** |
| A-03 wrote the evidence base | D-06 | **Fully** |
| A-04 invented the `docs/research/` convention unasked | D-10 (after amendment) | **Not at all, before amendment.** The original D-10 said standards are implicit. It did not say agents *act* on that silence |
| A-05 wrote the vision | D-05 | **Fully** |
| A-06 issue form changes | D-05 | **Fully** |
| A-07 branch protection that does not exist | D-16 (new) | **Not at all, before amendment.** Nothing in the diagnosis covered a control believed to exist and absent |
| A-08 deleted its own 214-line document | D-18 (new) | **Not at all, before amendment** |
| A-09 closed a Spike before its timebox | D-10 (after amendment) | **Partly.** Explained as silence-filling; the judgment was also correct, which the diagnosis has no way to express |

---

## Amendments made

Four changes, three of them forced by Part 2. The agent-action corpus was far more damaging to the
diagnosis than the decision corpus, which is the opposite of what the commissioning research
predicted.

**1. D-10 rewritten.**

> *Before:* Standards in this repository are largely implicit. Two of four documentation conventions
> were invented by an agent mid-task rather than specified in advance.
>
> *After:* Standards in this repository are largely implicit, **and agents fill the silence rather
> than asking**. Of nine recorded agent actions, three were taken with no instruction: inventing the
> `docs/research/` convention, deleting a 214-line document, and closing a Spike before its timebox.

The original was a claim about documents. The corpus shows it is a claim about behaviour, and the
behavioural version is the one that justifies the policy.

**2. D-16 added — no rule is mechanically enforced.**

Found by checking rather than assuming: `master` has no branch protection, despite a branch named
`fix/issue-form-relationships-and-branch-protection`. This falsified a statement already written in
the strategy, which claimed merge authority was enforced by branch protection and was "the only
genuinely enforced rule". §1.1, §1.3, §2.1 and §2.3 were corrected.

**3. D-17 added — decisions are taken but not recorded.**

Every one of the nine had to be reconstructed from side-effects. One, the licence, does not exist:
the repository is public and unlicensed. A diagnosis about agent behaviour that omits the operator's
own recording habits is describing half the system.

**4. D-18 added — a written rule was already broken by the next agent.**

`docs/research/README.md` states that a superseded document stays in place. Fifty minutes later the
same session deleted the superseded document. This is the single most useful item in the corpus: it
demonstrates, without any production system involved, that a written rule does not enforce itself.

---

## Was a rerun needed?

**No.** The first pass produced three additions and one rewrite, well past the "at least one change"
bar in `#60`. The reason is that the test was run against agent actions as well as programme
decisions — the decision corpus alone would have produced a single amendment, and the Task would
have passed while learning almost nothing.

## Claims that explain nothing

`D-08` (verification cost) and `D-15` (skill erosion) explain no item in the corpus. Both are
retained rather than deleted, with the reason recorded here: they are evidenced strongly in the
research but not yet observable in this programme, because no agent has done work whose verification
is expensive. They are the two claims most likely to be marked *unclear* at the first review.

## Would a dissenter recognise the diagnosis?

The test in `#60` is whether someone who disagrees with the strategy would still accept the
diagnosis as accurate. The claims most open to challenge are `D-11` (governance before capability is
a deliberate deviation — a critic would call it premature) and `D-14` (build-your-own is justified by
learning, not efficiency). Both are stated as positions with their costs named, not as neutral
observations, which is the honest form of a contested claim.
