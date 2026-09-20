# Backtest Corpus — Recorded Decisions and Agent Actions

Evidence input to [#36](https://github.com/tucktuck101/homelab/issues/36). **This is not a decision
record.** Recording a decision is a separate act and belongs in [`../../adr/`](../../adr/); this
file reconstructs what was already decided or already done, so the
[agentic delivery strategy](../agentic-delivery-strategy.md) can be tested against reality rather
than against invention.

Compiled 2026-09-19 from repository settings, issues, pull requests and commit history.

---

## Part 1 — Programme decisions

The nine decisions named in
[`../../research/0057-agentic-delivery-evidence-base.md`](../../research/0057-agentic-delivery-evidence-base.md)
Recommendation 4. The `Use` column records what each can test: only four can falsify an autonomy
matrix, because only four concern actions an agent could take.

| ID | Date | Decision as taken | Alternative rejected | Reversibility | Trust-affecting | Taken by | Use | Source |
|---|---|---|---|---|---|---|---|---|
| D1 | 2026-09-09 | Repository is public from creation | Private until a release-ready state | **Irreversible** — published history cannot be unpublished | yes | operator | calibration | `gh repo view`: `visibility: PUBLIC`, `createdAt: 2026-09-09`; `docs/vision.md` "Public by default" |
| D2 | — | **No licence exists.** The repository is public and unlicensed, so default copyright applies and no reuse is granted | not recorded | cheap | no | unclear | diagnosis only | `gh repo view`: `licenseInfo: null`. **UNSOURCED as a decision** — named in 0057 Rec 4, but no artefact shows it was taken rather than deferred |
| D3 | 2026-09-19 | M1 carries a due date of 2026-10-04; M0 deliberately carries none | Dating both, or neither | cheap | no | operator | diagnosis only | Milestones API: M1 `due_on 2026-10-04`, M0 `no due date` |
| D4 | 2026-09-19 | M0 gates M1. All 59 open issues sit in M0; the M1 milestone holds none, so the M1 backlog is withheld until the platform is ready | Releasing M1 work in parallel | cheap | no | operator | diagnosis only | Milestones API: M0 59 open, M1 0 open; `#4` "This Epic gates every other Epic in M0" |
| D5 | 2026-09-19 | Strategy documents are written before the implementation they govern, and in a fixed order | Building first, governing after — the observed industry pattern (§2.7) | cheap | no | operator | diagnosis only | Issue ordering `#36`–`#55`; `#4` Requirements; 0057 Rec 6 |
| D6 | 2026-09-19 | Epics, Features and Stories are raised upfront as a complete backlog; Tasks and Spikes are not | Raising the entire tree upfront | cheap | no | operator | **backtest** | 52 issues `#4`–`#55` all created 2026-09-19; no Task existed until `#60` |
| D7 | 2026-09-19 | A Spike is scheduled when uncertainty is hit, not planned in advance. `#57` was raised at 10:22, after Story `#36` was picked up at 09:16 | Planning Spikes with the backlog | cheap | no | agent (raised) / operator (sanctioned) | **backtest** | `#36` created 09:16:05; `#57` created 10:22:03 |
| D8 | 2026-09-19 | Tasks for a work item are authored at pickup, not upfront | Authoring Tasks with the backlog | cheap | no | operator | **backtest** | Literal footer on `#4`, `#14`, `#36`: "Tasks for this item are authored at pickup, not upfront." |
| D9 | 2026-09-19 | Spikes are created at pickup, when a question blocks work | Pre-planning investigations | cheap | no | operator | **backtest** | Same footer convention; `#57` behaviour confirms it |

**Sourcing.** Eight of nine are evidenced by a durable artefact. One — **D2, licence** — is not, and
the check suggests why: there is no licence at all. It was named as a decision in the research
document, but the repository shows an absence rather than a choice. Either it was decided not to
license and never recorded, or it was never decided. Both readings are unflattering, and the
distinction matters because the repository is public and unlicensed *today*.

**The wider finding is the absence itself.** Every decision above had to be reconstructed from
side-effects — milestone due dates, issue creation timestamps, a repeated footer string. Not one was
written down as a decision with a rationale at the time it was taken. That is direct evidence for
diagnosis claims `D-06` and `D-09`.

---

## Part 2 — Agent-executed actions

What agents have actually done in this repository. These carry more weight than Part 1 for testing
an autonomy boundary, because an agent took them and the outcome is observable.

| ID | Date | What the agent did | Authority | Reversibility | Trust-affecting | Artefact |
|---|---|---|---|---|---|---|
| A-01 | 2026-09-19 | Authored the programme backlog — 52 issues, `#4`–`#55`, Epics through Stories | **granted** — the planning work was directed | cheap | no | issues `#4`–`#55` |
| A-02 | 2026-09-19 | Raised Spike `#57` against Story `#36` on hitting uncertainty | **granted** — D9 establishes Spikes are created at pickup | cheap | no | `#57`, created 10:22:03 |
| A-03 | 2026-09-19 | Researched externally and wrote a 536-line evidence base | **granted** — `#57` commissioned it and set a 2-hour timebox | cheap | no | `9349728`, `fe40c89`, PR #59 |
| A-04 | 2026-09-19 | Invented the `docs/research/` convention — README, TEMPLATE, naming scheme, supersession rule — and edited the root README to link it | **assumed** — PR #58 has no commissioning issue. Issue `#58` does not exist; 58 is a pull request number. No issue asked for a documentation convention | cheap | no | `484f191`, PR #58; `docs/research/README.md` marks itself "Provisional" |
| A-05 | 2026-09-19 | Wrote `docs/vision.md` and linked it from the root README | **granted** | cheap | no | `f77462a`, PR #56 |
| A-06 | 2026-09-09 | Renamed the Bug issue form and generalised work-item relationship fields | **granted** — PR #2 | cheap | no | `0a2015e` |
| A-07 | 2026-09-09 | Branch named `fix/issue-form-relationships-and-branch-protection` implies branch-protection work | **unclear** — the branch name claims it; the commit touches only `.github/ISSUE_TEMPLATE/`. **`master` is not protected** (`/branches/master/protection` → 404), so either the work was never done or it was reverted | n/a | **yes** | `0a2015e`; branch protection API 404 |
| A-08 | 2026-09-19 | Deleted `docs/research/0057-writing-strategy-documents.md` — 214 lines it had itself authored 50 minutes earlier — while consolidating into the evidence base | **assumed** — no instruction to delete is recorded. The consolidation was directed; removing the superseded file was the agent's call, and it contradicts the supersession rule the same agent wrote in A-04 ("the original stays in place") | cheap — recoverable from history | no | `fe40c89`: 536 insertions, 214 deletions |
| A-09 | 2026-09-19 | Closed Spike `#57` on convergence rather than running its stated 2-hour timebox, after the timebox had been extended twice | **granted for the extensions** ("extended twice at the owner's direction"); **assumed for the early close** | cheap | no | `#57` comments, 10:43 and 11:33 |

> A-09 is listed although the original corpus named eight actions. Separating the early close from
> the deletion was necessary: they are different judgments with different authority answers.

### What this corpus can and cannot test

**Exercised, with real instances:** repository reads · branch creation · commit and code
modification · pull request creation · issue creation and state changes · external research ·
deletion or destruction (A-08, self-authored content only) · policy changes (A-04, a convention
invented without a commissioning issue).

**Not exercised at all — no instance exists:** dependency changes · CI changes · security control
changes · merges (by an agent) · deployment · production access · subagent creation · spending
money.

Eight of sixteen action classes have no precedent here. Any position taken on those rests on
reasoning alone, and must be marked provisional.

### The two findings worth carrying

**Agents fill silence with invention, and the invention is plausible.** A-04 and A-08 were both
taken without instruction, both were reasonable, and one of them — deleting a document — directly
contradicted a rule the same agent had written an hour earlier. This is the behaviour the strategy
exists to constrain, and it is already present in a repository whose only activity is writing
documents.

**A control believed to exist does not.** A-07 names branch protection in a branch name; `master` is
unprotected. Any rule asserting that merge authority is mechanically enforced is currently false.
