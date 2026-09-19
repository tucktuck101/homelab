# Agentic Delivery Strategy

| | |
|---|---|
| **Status** | Drafting |
| **Version** | 0.1.0-draft |
| **Owner** | @tucktuck101 |
| **Accepted** | Not yet — this document is not binding |
| **Plan ID** | `M0-E1-F1-S1` |
| **Commissioned by** | [#36](https://github.com/tucktuck101/homelab/issues/36) |
| **Evidence base** | [`../research/0057-agentic-delivery-evidence-base.md`](../research/0057-agentic-delivery-evidence-base.md) |
| **Update trigger** | Any claim in [Diagnose](#diagnose) becoming false. See [Refine](#refine). |
| **First review** | To be set on acceptance |

## Reading this document

Start at **Policy**. It states what you may and may not do; most readers need nothing else.
**Operations** says how each rule is enforced and how to get an exception. Everything below the
divider is the argument — *Refine*, *Diagnose*, *Explore* — and exists so the policy can be
challenged on evidence rather than on taste.

**What is deliberately missing in 0.1.** The autonomy boundary matrix — the per-action-class
statement of what an agent may do unsupervised — is **not written**. The reason is stated in
[§1.2](#12-autonomy-boundary--not-yet-written). An interim rule covers the gap. Nothing in this
version may be cited as a settled autonomy position.

---

# Policy

## 1.1 How policy is stated

Six conventions govern every rule in this document. They apply to the sections not yet written as
much as to the ones that are.

**Direction and guidance.** Every rule is one or the other.

| Marker | Keyword | Meaning |
|---|---|---|
| **Direction** | MUST / MUST NOT | Consistency matters more than judgment. No discretion. |
| **Guidance** | SHOULD / SHOULD NOT | The right path depends on context that cannot be anticipated. |

Direction is the default for agent-consumed rules. **Every guidance rule MUST name its escalation
path** — guidance with nowhere to escalate is an invitation to invent an answer, which is the
behaviour this document exists to remove. No other modal verbs carry normative weight; "may",
"can" and "will" are prose.

**Enforcement marking.** Every rule is marked `enforced` or `advisory`. In phase P0 there is no CI,
no test suite, no policy tooling and — verified on 2026-09-19 — no branch protection, so **every
rule in this version is advisory** and rests on the agent following it. This is stated plainly
rather than implied, because the first discovery that an assumed-enforced rule is not enforced
costs the document its credibility. That discovery has already happened once while writing this
version: see `D-16`.

**The tradeoff test.** Every rule states what it forbids and what that costs. A rule that forbids
nothing is deleted, not softened. Rules in this document carry their cost inline.

**Provisional positions.** A rule resting on no evidence is marked `provisional` and says so. This
programme has almost no delivery precedent, so provisional is a common and honest marking.

**Default-deny.** Where this document does not resolve a question, the agent does not resolve it
either. See [§1.3](#13-interim-rule-while-the-matrix-is-unwritten).

**Reversibility is the hard stop.** There is one physical host, no failover, and one reviewer. An
irreversible action is never authorised by an efficiency argument, however strong. *Forbids:*
trading safety for speed. *Costs:* agents will stop and wait on work they could probably have
completed correctly.

## 1.2 Autonomy boundary — not yet written

**Status: open. Owner: the operator. Blocking: nothing in this version depends on it.**

The matrix is meant to answer two questions for each class of action — *may an agent do this
unsupervised* (risk) and *should an agent be given this work at all* (efficiency) — and to do so as
a rule that also resolves classes nobody has enumerated yet.

It is not written in 0.1 because the inputs do not exist:

| Missing input | Consequence |
|---|---|
| No CI, tests or linters | `verifiability` is unmeasurable for every code-touching action class |
| No agreement rate between agent and operator judgment | The promotion criterion has no denominator. It is defined in `#66`, which is downstream of the matrix. |
| No run-cost tracking | Cost is evidenced as a top-three limiter elsewhere, and is unmeasured here |
| No delivery precedent outside documentation work | Eight of sixteen action classes have no instance in this repository: dependency changes, CI changes, security controls, agent merges, deployment, production access, subagent creation, spending. See [`evidence/0036-recorded-decisions.md`](evidence/0036-recorded-decisions.md) |
| No recorded operator positions | The decisions that would ground the risk axis were taken but never written down as decisions. All nine had to be reconstructed from side-effects, and one turned out not to exist |

Writing sixteen confident rows against that would be invention with a citation. Two things unblock
it, and both are scheduled rather than hoped for: the operator's standing positions, recorded as
decisions; and the first delivery precedent that exercises an action class other than writing
documents.

Until then, [§1.3](#13-interim-rule-while-the-matrix-is-unwritten) applies.

## 1.3 Interim rule while the matrix is unwritten

**Direction · advisory.** An agent MUST treat any action not explicitly authorised by its own issue
as **recommend-only**: it prepares the change, states what it would do, and stops. It MUST NOT
execute.

**Direction · advisory.** An agent MUST NOT take an irreversible or trust-affecting action under any
circumstances in this version. That includes, without limitation: merging, deleting anything it did
not create in the current Task, changing repository settings or security controls, publishing,
deploying, granting access, or spending money.

**Direction · advisory.** Merge authority rests with the operator, absolutely. An agent MUST NOT
merge its own work or another agent's, in any repository, under any exception.

**This rule is not enforced.** `master` carries no branch protection — verified 2026-09-19, the
protection API returns 404 — so nothing rejects a push. **No rule in version 0.1 is mechanically
enforced.** Protecting the branch is owned by `#42`; until it lands, merge authority rests on the
agent obeying this sentence.

*Forbids:* every action whose authority is ambiguous — which, in this version, is most of them.
*Costs:* agents will stop on work they were plainly competent to complete, and the operator absorbs
the interruption. That cost is accepted deliberately for one reason: the failure mode it prevents is
irreversible on a single host, and the failure mode it creates is an interruption.

## 1.4 Concurrency and exclusive resources

**Direction · advisory.** Execution within a Story is **sequential by default**. An agent MUST NOT
start a Task in a Story where another agent holds an incomplete Task, unless every condition in the
parallel test below is true.

**Parallel test — all four MUST hold:**

1. The Tasks name disjoint output files. Two agents writing one file is not a merge conflict to be
   resolved; it is work to be redone.
2. Neither Task declares an exclusive resource the other also declares.
3. Neither Task's stated dependencies name the other.
4. Neither Task changes a rule, convention or interface the other consumes.

If any condition is false or cannot be determined, the agent MUST treat the work as sequential.
*Forbids:* optimistic parallelism on shared state. *Costs:* throughput. Independent work sometimes
waits for no reason other than that its independence could not be proven cheaply.

**Exclusive resources.** A resource is exclusive when concurrent use can corrupt it or produce a
result that depends on timing. In this programme that is: the physical host, repository settings,
any long-running process bound to a fixed port, and any single file under concurrent edit.

**Direction · advisory.** A claim on an exclusive resource MUST be recorded on the issue that holds
it, before first use, naming the resource and the holding agent. An agent MUST verify no live claim
exists before starting. On completion — successful or not — the holder MUST release the claim in the
same place.

**Direction · advisory.** A claim whose holding Task is closed, abandoned, or has produced no
activity for the stated claim window is **stale**. A stale claim MUST be broken by the operator, not
by the waiting agent. *Forbids:* an agent judging another agent dead and seizing its resource.
*Costs:* a crashed agent blocks its resource until a human notices. Accepted: the alternative is two
agents on one host, each believing the other is gone.

**Guidance · advisory.** Work requiring the physical host SHOULD be batched into as few claims as
possible rather than acquired and released repeatedly. *Escalation:* if batching would make a change
too large to review in one pass, keep the batches small and raise the contention on the Story — batch
size wins over claim count, because review capacity is the binding constraint.

## 1.5 Handoff

**Direction · advisory.** A handoff MUST carry all of, and only, the following:

1. The issue number the receiving agent owns.
2. The durable documents that govern it, **by reference** — path and section, never pasted content.
3. Any exclusive-resource claim being transferred, named explicitly.
4. What has already been done, as artefacts: commits, files, issue comments.
5. What was attempted and abandoned, with the reason.

**Direction · advisory.** A receiving agent MUST NOT assume: that the sending agent's conclusions
were verified; that work described as done is present in the repository; that authority held by the
sender transfers; or that context absent from the handoff is unimportant. It MUST verify claimed
artefacts exist before building on them.

*Forbids:* narrative handoff, where the receiver inherits the sender's beliefs along with its
output. *Costs:* re-verification the receiver could often have skipped.

## 1.6 Parent-context inheritance

**Direction · advisory.** A child agent MUST be given context **by reference** — issue numbers, file
paths, document sections — and MUST NOT be given a copy of the parent's accumulated working state.
References stay correct when the underlying artefact changes; copies silently rot.

**Direction · advisory.** A child MUST NOT hold authority the parent does not hold. Authority is
never created by delegation. *Forbids:* the laundering pattern, where a constrained agent spawns an
unconstrained one to do what it may not. *Costs:* a child sometimes cannot complete work a human
would have authorised, and must escalate through its parent.

**Direction · advisory.** A child agent's output is a **proposal to its parent**, not a completed
change. The parent MUST verify it against the child's stated acceptance criteria before building on
it or reporting it complete.

## 1.7 Scope expansion

An agent will find defects outside its Task. What it does about them is decided here, not in the
moment.

**Direction · advisory.** On finding a defect outside its current Task, an agent MUST apply this
test in order:

| Condition | Action |
|---|---|
| The defect blocks the current Task, and the fix is reversible and inside the Task's declared outputs | Fix it. Record it in the Task's evidence. |
| The defect blocks the current Task, and the fix is outside the declared outputs or is irreversible | **Stop.** Record it, raise it, escalate. Do not fix. |
| The defect does not block the current Task | **Record and continue.** Raise it as an issue. Do not fix it, however small. |
| The defect is in a rule, convention or strategy document | **Stop and escalate.** Policy changes are never in scope for a Task that did not ask for one. |

*Forbids:* the drive-by fix — the single most common way an agent's change becomes unreviewable.
*Costs:* known defects stay broken while an issue is raised, and the operator absorbs more triage.

**Direction · advisory.** "Record" means an issue exists, linked to the Task that found it. A defect
mentioned only in an agent's final message is not recorded.

---

# Operations

*Above this line is instruction. Below it is argument. Most readers stop here.*

## 2.1 Enforcement and breach

**In phase P0 there is no CI, no test suite and no policy tooling.** One rule in this document is
mechanically enforced; every other rule depends on the agent following it and on the operator
noticing when it did not.

| Rule | Marker | Enforcement | On breach |
|---|---|---|---|
| Merge authority rests with the operator (§1.3) | direction | advisory — **intended to be enforced, currently is not**; `master` is unprotected, owned by `#42` | Operator reverts; the breach is an incident, not an exception |
| Recommend-only for unauthorised actions (§1.3) | direction | advisory | Revert; record in the ambiguity log; the gap is a defect in this document |
| No irreversible or trust-affecting actions (§1.3) | direction | advisory | Stop work; operator assesses blast radius before anything else proceeds |
| Sequential by default (§1.4) | direction | advisory | Discard the losing branch's conflicting work; do not hand-merge |
| Exclusive-resource claims (§1.4) | direction | advisory | Operator breaks the claim and records why |
| Host work batched into few claims (§1.4) | guidance | advisory | Escalate on the Story |
| Handoff contents and assumptions (§1.5) | direction | advisory | Receiver rejects the handoff and returns it |
| Context by reference; no inherited authority (§1.6) | direction | advisory | Child output rejected unverified |
| Scope-expansion test (§1.7) | direction | advisory | Out-of-scope change reverted, then raised as its own issue |

**Direction · advisory.** An unmarked rule anywhere in this document is a defect, not a permission.
An agent encountering one MUST treat it as direction and advisory, and record the omission.

## 2.2 Exceptions

**Direction · advisory.** An exception MUST be requested before the action, never after. A breach
reported afterwards is a breach, not an exception.

An exception request states: the rule, the specific action, why the rule should not apply here, the
blast radius if the judgment is wrong, and the expiry.

**Approval.** The operator approves. There is no second reviewer; approval is contractual, not
procedural. An agent MUST NOT approve its own exception, and MUST NOT approve another agent's.

**Expiry is mandatory.** Every exception carries one. The default is **the Task that requested it**;
the maximum without explicit re-approval is **one milestone**. An expired exception reverts
automatically — the rule applies again with no further action. *Forbids:* the standing exception.
*Costs:* recurring legitimate exceptions must be re-requested, which is friction by design.

**Three strikes.** The same exception granted three times means **the exception is the policy**. The
rule MUST be amended rather than exempted a fourth time. This is a hard trigger, not a judgment.

**Recording.** Every exception — granted or refused — is recorded in
[`logs/exceptions.md`](logs/exceptions.md). An unrecorded exception did not happen, and cannot count
towards three strikes.

## 2.3 Coverage and deferrals

The Epic (`#4`) names fourteen areas. This version addresses five, defers eight to their owning
issues, and leaves one open by choice.

| # | Area | Status | Where |
|---|---|---|---|
| S01 | Agent autonomy boundaries and decision authority | **Open — not written** | §1.2, with the interim rule in §1.3. Blocked on recorded operator positions and on precedent. Decision authority defers to `#16`. |
| S02 | The Task execution model | Deferred | The execution contract, `#37` — it is operational mechanism, not policy |
| S03 | Uncertainty and Spike escalation | Deferred | `#15`. This document must not pre-empt the escalation model it will define. |
| S04 | Parent-context inheritance | **Addressed** | §1.6 |
| S05 | Concurrency and exclusive resources | **Addressed** | §1.4 |
| S06 | Agent-to-agent handoff | **Addressed** | §1.5 |
| S07 | Evidence expectations | Deferred | `#32` evidence and auditability; conventions in `#20` |
| S08 | Failure and blocked-work handling | Deferred | `#15` — a blocked agent is an escalation case |
| S09 | Human Review | Deferred | `#16` decision authority and human review model |
| S10 | Merge authority | **Addressed** | §1.3 — stated absolutely; enforcement is absent and owned by `#42` |
| S11 | Scope-expansion rules | **Addressed** | §1.7 |
| S12 | Self-review versus independent review | Deferred | `#16`. Note the standing constraint: there is no independent reviewer, so "independent" cannot mean a second human. |
| S13 | How agents discover Ready work | Deferred | `#19` work discovery and Project automation |
| S14 | Repository governance strategy | Deferred | `#17` governance strategy, applied by `#42` |

**Direction.** A deferral is a pointer, not a silence. If an agent needs a deferred area resolved in
order to act, that is an escalation, and the absence MUST be recorded in
[`logs/ambiguities.md`](logs/ambiguities.md) so the gap is visible rather than worked around.

---

# Refine

The load-bearing evidence. Only what changed a decision appears here; the full record is in the
[evidence base](../research/0057-agentic-delivery-evidence-base.md).

**The binding constraint is review capacity, not model capability.** DORA's analysis of Google
engineers found that time saved generating code is re-allocated to verification and prompting
overhead, and that because models cannot signal uncertainty, engineers treat every interaction as
potentially deceptive. In a team, the verification tax shifts cost from author to reviewer. Here
there is one person in both roles, so it does not shift — it accumulates. This is why §1.4 prefers
small batches over fewer claims, and why §1.7 forbids the drive-by fix: both protect review
capacity, which is the scarce resource.

**Structure predicts outcomes more strongly than tooling does.** Formal governance correlates with
94% trust in AI output against 51% for ad hoc; assurance-ready finance functions report three to six
times the rate of significant improvement. DORA's amplifier thesis is the same claim: AI magnifies
the strengths of high-performing organisations and the dysfunctions of struggling ones. The reading
this document takes is that rules written before capability arrives are cheaper than rules written
after an incident — which is the argument for M0 existing at all.

**Nobody grants full unsupervised autonomy.** Across 250 security operations centres, autonomy runs
on a staged ladder and no respondent grants full autonomy; 57% require human review of every AI
verdict. This is the strongest available evidence that §1.3's recommend-only default is normal
practice rather than excessive caution, and it is why no version of this strategy will contain a
"fully autonomous" tier.

**Self-assessment of AI productivity is unreliable by roughly 40 points.** Developers in METR's
controlled trial forecast a 24% speedup, were measured 19% slower, and still believed afterwards
they had been sped up by 20%. The number matters less than the direction: instinct is not evidence.
This is why the efficiency axis in §1.2 is blocked on measurement rather than written from
judgment.

**Large organisations do not decide the boundary in advance.** 85% run agents that execute without
real-time human involvement, 49% have not updated governance for agentic AI, 47% have bypassed their
own process, and assurance later modifies, pauses or stops a quarter of systems or more. Deciding
in advance is the deviation this programme is taking, deliberately, because it has one host and no
capacity to absorb a discovered incident.

**Building your own agent tooling is a known failure mode.** 72% of AI-using SOCs attempted internal
LLM tooling; 46% of those deprecated it, replaced it or never reached production — with **no speed
advantage** over buying. This programme is partly a build-your-own exercise. That is legitimate as
learning, and it is in the vision. It must not be justified by expected efficiency.

## Update triggers

| Trigger | Door | Cost |
|---|---|---|
| A claim in [Diagnose](#diagnose) becomes false | **New phase** — back to drafting | Expensive, rare |
| A policy is wrong but the diagnosis holds | **Amend** — stays Active | Cheap, expected |
| The same exception granted three times | **Amend** — the exception is the policy | Cheap |
| This document cannot resolve a real decision | **Amend** if isolated; **new phase** if clustered | Depends |
| A constraint is lifted or arrives | **New phase** — constraints are the diagnosis skeleton | Expensive |
| The diagnosis is solved or superseded | **Retire** with a forward link | One paragraph |

**Not triggers:** time passing; learning something interesting that does not falsify a claim;
disagreeing with a rule — that is what exceptions are for.

**Still to be defined:** the agreement rate between agent conclusions and operator judgment, its
sampling method, and the threshold at which autonomy widens. It is owned by `#66` and is a
precondition for writing §1.2.

---

# Diagnose

The situation as it is. Aspiration is in [`../vision.md`](../vision.md) and does not belong here.

Each claim is individually markable **true / false / unclear**. The update trigger for this document
is any of them becoming false, which is why they are written as claims rather than prose.

| # | Claim | How to check |
|---|---|---|
| D-01 | There is one operator and no independent reviewer. Every approval gate is contractual, not procedural. | Count people with write access |
| D-02 | Delivery runs on a single physical host with no failover. A destructive action against it is not recoverable by switching to another. | Inventory the hosts |
| D-03 | The repositories are public while the work is in progress, so exposure is immediate rather than deferred to a release. | Repository visibility setting |
| D-04 | There is no CI, no automated test suite and no policy tooling. Every rule written now is advisory. | Absence of workflows in `.github/` |
| D-05 | Agents, not humans, are the primary consumers of this document. Anything left unstated is inferred by a model rather than asked about. | Who reads it: check what cites it |
| D-06 | No delivery precedent exists in this programme. This strategy is being written earlier in its evidence cycle than the literature recommends, and version 1 will be wrong in specifics. | Count merged Story PRs that changed anything other than documentation |
| D-07 | Every agent action taken in this repository so far has been documentation work. No agent has changed a dependency, a workflow, a security control or a deployed system. | `git log` by file path |
| D-08 | Time saved by generating code is re-spent on verification and prompting, and that cost lands on the same person who saved it. | Recorded time per agent-run Story, once measured |
| D-09 | Context an agent needs is frequently undocumented rather than unavailable — it exists in the operator's head and nowhere else. | Count clarifying questions per Task |
| D-10 | Standards in this repository are largely implicit, and agents fill the silence rather than asking. Of nine recorded agent actions, three were taken with no instruction: inventing the `docs/research/` convention, deleting a 214-line document, and closing a Spike before its timebox. | `git log` for `484f191` and `fe40c89`; `#57` comments; absence of a commissioning issue for PR #58 |
| D-11 | Governance is being written before the capability it governs exists, which is the opposite of the observed industry pattern and is a deliberate deviation. | This document's position in the milestone |
| D-12 | Run cost is unmeasured and unbudgeted, while cost is evidenced elsewhere as a top-three limiter on agent use. | Absence of any cost record |
| D-13 | Agent failure modes, telemetry and containment are scoped by no Epic in this programme. Agents are treated as a tool, not as an operated component. | Search the Epic scopes for agent observability |
| D-14 | Building delivery tooling in-house has a high evidenced abandonment rate and no measured speed advantage. This programme is doing it anyway, justified by learning rather than efficiency. | `../vision.md`, "What This Is Proving" |
| D-15 | Skill erosion is a real cost of this operating model, volunteered consistently by practitioners rather than prompted, and nothing in this programme currently measures or resists it. | Absence of any countermeasure in M0 scope |
| D-16 | No rule in this programme is mechanically enforced. `master` has no branch protection, despite a branch named for adding it, so the one control assumed to exist does not. | `GET /repos/tucktuck101/homelab/branches/master/protection` returns 404 |
| D-17 | Decisions are taken but not recorded. All nine programme decisions had to be reconstructed from side-effects — milestone dates, issue timestamps, a repeated footer string — and one, the licence, turned out never to have been taken: the repository is public and unlicensed. | [`evidence/0036-recorded-decisions.md`](evidence/0036-recorded-decisions.md) Part 1; `gh repo view --json licenseInfo` |
| D-18 | An agent has already violated a rule another agent wrote, within an hour of it being written: the `docs/research/` supersession rule says the original stays in place, and the superseded document was deleted. | `docs/research/README.md` "Status and Supersession"; `fe40c89` shows 214 deletions |

**D-06, D-07, D-10, D-12, D-13, D-14, D-15, D-16, D-17 and D-18 are the uncomfortable ones.** They
are load-bearing. D-06 and D-07 are why §1.2 is unwritten. D-12 is why cost belongs in the
efficiency axis. D-16 is why every rule here is marked advisory rather than assumed. D-10, D-17 and
D-18 are the core of the case for this document existing at all: agents already fill silence with
plausible invention, decisions already evaporate unrecorded, and a written rule was already broken
by the next agent to touch the repository. None of that required production access or a deployment
to happen — it happened while writing documents.

---

# Explore

What was brought in, and what was rejected.

The evidence base behind this document covers three questions: what a strategy document is and how
to write one; where agent use stops being efficient; and what pains appear when agents are used
first rather than occasionally. Strategy craft draws on Rumelt's kernel as applied to engineering by
Will Larson, and Roger Martin's definition of strategy as choice. The efficiency question draws on
METR's controlled trial and its follow-ups, DORA 2025, Gartner and EY. The pain evidence is 2026
surveys across software, platform, support, security, finance and design.

**Rumelt's *Good Strategy / Bad Strategy* (2011) was not read directly.** It is cited throughout via
Larson's engineering-specific application. Several other figures were excluded for lack of a primary
source; they are listed in the evidence base rather than repeated here.

**Nothing in the consulted material addresses agents as readers of governance documents.** Every
source assumes human readers, teams, reviewers and budgets. Where this document treats agents as the
primary audience, that is invention, not adoption.

| Approach considered | Rejected because | Source |
|---|---|---|
| A binary permitted / forbidden autonomy split | Collapses two independent questions. Work can be permitted and still be a waste of the agent and the reviewer. | Evidence base, Rec 7 |
| A single risk axis | Same defect, and it produces authorised waste invisibly — nothing flags work an agent may do but should not be given. | Rec 7 |
| A fully autonomous tier | No surveyed organisation grants one, including those with far more review capacity than this programme has. | §3.2 |
| Deciding the boundary after deployment, via assurance | The observed enterprise pattern, and it depends on absorbing incidents and retiring systems. One host and one operator cannot absorb a discovered incident. | §2.7 |
| Writing the sixteen-row matrix now, marking the unknowns provisional | Twelve provisional rows is a guess wearing a label, and every downstream document would cite it as settled. | §1.2 |
| Building a strategy document template first | Templates written in advance accumulate requirements until writing one is prohibitive. Write the first document, see which sections did work, then derive the template. | §1.10 |
| One combined strategy and contract document | They change at different rates and have different audiences. The split maps onto policy versus operations. | `#14`, Rec / boundary |
| Writing all fourteen M0 strategy documents at one altitude | Far more people fail by attempting too much strategy than too little. Mitigation is lower altitude and higher permissiveness, sequenced, not abandonment. | Rec 6 |
| The full RFC 2119 keyword set | Unnecessary precision for two distinctions. MUST and SHOULD carry direction and guidance; the rest add interpretation load for no gain. Whether keywords help agent readers at all is untested. | Evidence base, Confidence and Gaps |
| Treating documentation precedent as delivery precedent | Eight agent actions, all document writing, exercise perhaps five of sixteen action classes. Generalising from them would overstate what is known. | D-07 |
