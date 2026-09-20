# Strategy

Strategy documents explain how this programme works and why it works that way. They are written
for a person who needs to make a decision and wants to know what the sensible answer is, and what
it rests on.

## What a strategy document is here

A short piece of documentation. Two to four pages is the working expectation, and a strategy that
runs much longer has usually stopped being a strategy.

It should contain the situation as it actually is, the position taken, and the reason for that
position. It should say what it is unsure about. It should be readable in one sitting by someone
who was not involved in writing it.

## What a strategy document is not

It is not a specification, a procedure, or a set of rules to be evaluated clause by clause. If a
document is being written so that it can be applied mechanically, it has changed genre and belongs
somewhere else.

The first strategy written here learned this the expensive way. It grew to roughly a thousand
lines of ordered tests, defined terms and per-case conditions, driven by repeatedly asking whether
an agent could misread it. That is a reasonable question to ask of a contract and the wrong
question to ask of a strategy, and answering it produced a document nobody wanted to maintain. It
was replaced by a version about a fifth the length. The history is in git if the detail is ever
needed.

Practically, the following are signs a strategy document has drifted:

- numbered rules that are meant to be applied in order
- a glossary of terms defined for the document's own use
- procedures naming specific commands or flags
- tables enumerating cases rather than explaining a principle
- supporting files that exist only to demonstrate the document is self-consistent

Any of these may be legitimate somewhere. None of them belongs here.

## Where other things go

| Content | Goes |
|---|---|
| What the programme is for | [`../vision.md`](../vision.md) |
| A single decision and its reasoning | [`../adr/`](../adr/) |
| Evidence gathered while reducing uncertainty | [`../research/`](../research/) |
| How the system is built | [`../architecture/`](../architecture/) |
| Step-by-step instructions | The runbook or procedure itself |
| Progress and status | The issue |

Supporting evidence for a strategy may live in `evidence/`, prefixed with the issue that produced
it. Keep it to material the strategy actually rests on.

## Status

Each document carries a status in its header: **Draft** while it is being written, **Active** once
it is the position the programme follows, **Retired** when it no longer is, with a note saying why.

Retired documents stay where they are. A superseded document is not edited to look correct in
hindsight.

## Amending

Change a strategy when something it asserts stops being true, when a position it takes gets in the
way repeatedly, or when it fails to answer a question it should have answered. Record what changed
and why. Do not change it because time has passed, and do not extend it to cover a case it was
never meant to decide.

Agents may draft strategy documents and amendments. They do not adopt them.
