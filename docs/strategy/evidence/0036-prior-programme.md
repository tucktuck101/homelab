# Prior Programme — Recorded Failures

Evidence input to [#36](https://github.com/tucktuck101/homelab/issues/36). Five conventions in
[`../agentic-delivery-strategy.md`](../agentic-delivery-strategy.md) §1.1 and the guiding policy's
central claim in §1.0 derive from failures measured in a **different** programme:
`launchpad-26/buzz`, a multi-contributor agentic delivery fork operated during 2026.

**Why this file exists.** Those records live in that repository, not this one. An agent reading only
this repository could not verify the claims, and a strategy whose own thesis is *evidence is not
authority* must not cite what its reader cannot reach. This file states what was measured, where the
record is, and what could not be verified from here.

**Status.** Secondary. Every figure below is quoted from that programme's own decision records and
was read at source on 2026-09-19; none has been independently re-measured here, and the source
repository is not public to this project's readers.

---

## The figures the strategy relies on

| Claim | Figure | Source record |
|---|---|---|
| A review queue exceeding capacity was cleared by bypassing the gate | **132 pull requests** merged with admin bypass past **77** changes-requested reviews and unresolved CI, 2026-08-28 | ADR-0052 |
| Most of those merges were never checked | GitHub started **10 workflow runs for 103 merges** | ADR-0052 |
| Review state carried no provenance | **0 of 1,064** reviews contained structured provenance; **72%** could not be attributed to human or agent without heuristics | PRD #2006 |
| Blocking had no consistent meaning | Two reviewers used `CHANGES_REQUESTED` for blocking findings **60.7%** and **5.0%** of the time | PRD #2006 |
| Trivial findings consumed the blocking mechanism | Of 116 change-request reviews, **57** were creation-time artefacts and **29** described their own finding as trivial | PRD #2006 |
| The gate collapsed routinely, not once | **131 of 331 merges (39.6%)** happened with checks failing; **97** by the repository owner | PRD #2006 |
| Model verdicts are not checks | Model verdict reliability measured at **AUROC 0.48–0.64** against 6,642 human-verified labels | ADR-0019, quoting arXiv:2603.06594 |
| Building your own agent tooling has a poor record | **72%** of AI-using SOCs attempted internal LLM tooling; **46%** of those deprecated it, with no speed advantage | `../../research/0057-agentic-delivery-evidence-base.md` §3.6 — this one *is* verifiable here |

## The diagnosis that matters more than the figures

ADR-0052's own reading of 2026-08-28:

> "That is the failure this record exists to stop recurring — **not the bypass itself, but the
> condition that made bypass the only available move.**"

Three rules combined to produce it: one issue per pull request, against Features carrying 15–41
children; draft everything and approve nothing, making every one a human touch; and a blocker stops
a merge, adding a re-review round for defects a follow-up commit fixes more cheaply. Agent
throughput was capped by human review capacity, and when the cap bound, the gate was discarded.

**This is the evidence behind §1.0's prohibition on widening authority to clear a bottleneck.** The
prior programme's response was to widen authority; this one's is to make verification cheaper. That
is a deliberate divergence from a programme that had more reviewers, more platform enforcement and
more slack than this one does.

## Which conventions came from where

| §1.1 convention | Origin |
|---|---|
| Three outcomes; `indeterminate` never renders as `pass` | ADR-0008 — an audit that could not distinguish *disabled* from *unauthorised* reported `indeterminate`; *"`indeterminate` must never render as `pass`"* |
| Never manufacture a successful outcome | RQA requirements RQA-FR-011/028/037; ADR-0061 — a review without verdict authority escalates, never completes |
| Replay, never self-authorise | ADR-0037 (replay-only conflict resolution), ADR-0064 (closed tool registry, exact paths), ADR-0065 (conformance before content) |
| Authority comes only from a live operator statement | PRD #2006 security implications; ADR-0048 (upstream content containment) |
| Every exception is two named conditions | ADR-0036 — the security-hotfix escape required a CVSS ≥ 7.0 advisory **and** a change touching only the files that fix names |

## Not verified from here

- None of the buzz figures has been independently re-measured in this programme.
- The AUROC figures are quoted by ADR-0019 from a paper that record itself did not verify.
- That programme had multiple contributors, platform-enforced branch protection, push restrictions
  and required approvals. **None of those exists here**, so its measurements describe a system with
  more controls than this one, not fewer. Where a control is cited as having failed there, it is at
  least present there and absent here.
