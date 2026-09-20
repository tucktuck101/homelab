# Decisions Log

Every **classifier verdict** an agent reaches, and the agreement datum where one was sampled. This
is the measurement frame defined in
[§2.3](../agentic-delivery-strategy.md#23-measurement--the-agreement-rate), and the only basis on
which a row in §1.2.2 may be promoted.

**One line per verdict, recorded before the agent acts.**

## What belongs here

**Every verdict**, not the clean ones. That includes verdicts that resolved to `P` and stopped,
verdicts that escalated, verdicts the agent marked `indeterminate`, and verdicts the operator
overruled in either direction.

A log holding only the decisions the strategy settled cleanly would measure the easy half and
report a high number that means nothing. §2.3.2 states this as direction for that reason.

## Sampling

One verdict in five is sampled, plus **every** verdict in a class under consideration for
promotion. For a sampled verdict the operator records their own answer in `Operator level`
**before seeing the agent's** — an operator shown the agent's answer first is anchored by it, and
the result measures agreement with a suggestion rather than with a judgement.

`Agrees` is `yes` only where the two levels are identical. **An agent more cautious than the
operator disagrees**, and the disagreement is recorded as `agent narrower`; wider is recorded as
`agent wider`, which resets that class's promotion count to zero.

| Date | Action | Class | Test | Agent level | Sampled | Operator level | Agrees |
|---|---|---|---|---|---|---|---|

_No entries. The strategy became `Active` at 1.0.0 on 2026-09-19; verdicts are recorded from the
first Task worked under it._

## Rate

```text
agreement rate (class C) = agreeing sampled verdicts in C / sampled verdicts in C
```

Per class, never programme-wide. Promotion needs ≥ 20 sampled verdicts in that class, ≥ 90%
agreement, and no `agent wider` disagreement in the sample — §2.3.5.

## Pre-strategy baseline

Decisions taken before this document existed are in
[`../evidence/0036-recorded-decisions.md`](../evidence/0036-recorded-decisions.md). They are
evidence, not entries: the operator settled them, not the strategy, and they carry no agreement
datum.
