---
issue: "#57"
title: How to write a strategy document
date: 2026-09-19
status: current
supersedes:
superseded_by:
---

# Research: How to write a strategy document

## Question

How do you write a strategy document, when you have never written one? Specifically:

1. What is a strategy document, and what does a good one do that a bad one doesn't?
2. What goes in one, and why is each part there?
3. What is the process for producing one, start to finish?
4. What do real ones look like?
5. What do beginners get wrong?
6. How do you know when yours is good enough?

## Why It Was Asked

`#36` requires an agentic delivery strategy, and thirteen further strategy and policy documents follow it in Milestone 0. The author has not written one before. Without an acquired model of what the artefact is and how it is produced, every one of those documents is guesswork, and the Epic's success criterion — that an agent can act correctly from its issue plus the linked documents — cannot be assessed.

## Scope

**Investigated:** the definition of strategy and its failure modes; document anatomy; the production process; four published worked examples; quality evaluation. Sources are predominantly Will Larson's *Crafting Engineering Strategy* (2025), which is published in full online and applies Richard Rumelt's framework specifically to engineering, plus Rumelt's kernel and Roger Martin's definition of strategy as choice.

**Not investigated:** RFC 2119 normative keyword conventions and machine-readable rule formats; policy-as-code; how compliance documents mark enforceability; academic strategic-management literature. These were deliberately excluded as second-order — they matter for expressing rules, not for understanding what the document is. Several remain open and are listed under Gaps.

**Timebox:** 2 hours. The work stopped because the material converged, not because time ran out — the sources agree substantially, and further reading produced repetition.

## Findings

### 1. A strategy is a decision-making instrument, not a statement of intent

Three definitions converge.

Rumelt's kernel holds that a strategy has three parts: a **diagnosis** (a theory of the nature of the challenge), a **guiding policy** (the approach chosen to grapple with it), and **coherent action** (the specific actions that follow). Larson summarises it as: *"a strategy is only meaningful if it leads to aligned action"* ([Writing an engineering strategy](https://lethain.com/eng-strategies/), 2023-02-13).

Martin's definition is narrower and sharper: *"strategy is choice. Strategy is not a long planning document; it is a set of interrelated and powerful choices that positions the organization to win"* ([rogerlmartin.com](https://rogerlmartin.com/thought-pillars/strategy), consulted 2026-09-19).

Larson's own working definition across *Crafting Engineering Strategy* is the bluntest: strategy is **"making decisions"**, and more precisely *"the art of reproducibly making good decisions"* ([craftingengstrategy.com](https://craftingengstrategy.com/), consulted 2026-09-19).

Two consequences follow, and both are load-bearing.

**Every organisation already has a strategy, written or not.** Larson: *"all companies follow some strategy, even if it's undocumented … Your engineering strategy is how you approach your current challenges"* ([Steps to build an engineering strategy](https://lethain.com/components-of-eng-strategy/), 2025-03-27). Writing one is therefore an act of *documenting and improving* an existing practice, not conjuring one from nothing.

**A guiding policy that implies no tradeoff is not a policy.** Larson is explicit: *"Guiding policies are typically going to be implicit or explicit tradeoffs … If a guiding policy doesn't imply a tradeoff, you should be suspicious of it (e.g. 'working harder to get it done' isn't really a guiding policy)"* ([Writing an engineering strategy](https://lethain.com/eng-strategies/)).

The single most useful test found in this research is therefore: **for each statement, what does it forbid, and what does it cost?** A statement that forbids nothing is not strategy.

### 2. Good strategy is boring, and easier to write than bad strategy

This finding was unexpected and is worth stating plainly, because it contradicts the intuition that a strategy document should be impressive.

Larson, quoting Camille Fournier: *"writing about engineering strategy is hard because good strategy is pretty boring … when people hear 'strategy' they think 'innovation'"*. His own position: *"The reality is that good engineering strategy is boring, and that it's easier to write an effective strategy than a bad one"* ([Write five, then synthesize](https://lethain.com/good-engineering-strategy-is-boring/), 2020-11-26).

On policy quality specifically: *"With an excellent diagnosis, your policies will often feel inevitable, and perhaps even boring. That's great: what makes a policy good is that it's effective, not that it's novel or inspiring"* ([Setting policy for strategy](https://lethain.com/policy-for-strategy/), 2025-03-13).

The corollary is that strategies worth writing often feel too obvious to bother writing: Larson names *"When should we write design documents?"* and *"Which databases do we use for which use cases?"* as examples of strategies worth writing.

### 3. Anatomy: five components, written in one order and read in another

Larson's five components ([Steps to build an engineering strategy](https://lethain.com/components-of-eng-strategy/)):

| Component | What it does |
|---|---|
| **Explore** | Survey how others have approached this problem, before committing to an approach |
| **Diagnose** | Understand your own situation and constrain the problem, before solving it |
| **Refine** | Test the raw ideas against reality — strategy testing, systems modelling, Wardley mapping |
| **Policy** | The decisions and tradeoffs that address the diagnosis |
| **Operations** | The concrete mechanisms that turn policy into an active force |

Each is an input to the next: exploration feeds diagnosis, diagnosis narrows the infinite space of possible policies, operations make policy real rather than "an abstract treatise".

**The reading order is the reverse of the writing order.** This is the most immediately actionable finding in the research. Larson recommends publishing as: **Policy → Operation → Refine → Diagnose → Explore** ([Making engineering strategies more readable](https://lethain.com/readable-engineering-strategy-documents/), 2024-05-18).

His reasoning: *"The vast majority of strategy readers want the answer, not to understand the thinking behind the answer, and these are your least motivated readers."* Writing-order documents fail in three specific ways — readers give up before reaching the policy and conclude there is no clear direction; approval meetings get derailed into debating research rather than the proposal; and if you strip the thinking out entirely to fix this, future readers cannot trace the reasoning and conclude *"I guess the previous engineers here were just dumb."*

**The structure is not sacred.** *"You should discard every element of strategy that gets in your way as long as you can explain what that element was intended to accomplish."* The published example strategies each refactor it — the user-data strategy folds Operation into Policy and embeds Refine within Diagnose, and states so in a short "Reading this document" preamble.

### 4. Policy has four recurring shapes

From [Setting policy for strategy](https://lethain.com/policy-for-strategy/):

- **Approvals** — the process for making a recurring decision (who must be consulted, and how). Example: *"Exceptions must be granted in writing by CISO."*
- **Allocations** — how resources split across investments. *"the most concrete statement of organizational priority."*
- **Direction** — explicit instruction on how a decision **must** be made. Appropriate *"for problems you understand clearly, and you value consistency more than empowering individual judgment."* Example: *"all new code must be written in the monolith."*
- **Guidance** — a recommendation on how a decision **should** be made. For when *"you can explain the desired destination, but you can't mandate the path to reaching it."*

The direction/guidance distinction is the practitioner equivalent of a MUST/SHOULD split, arrived at from the opposite direction: you choose direction when consistency matters more than judgment, and guidance when the path genuinely depends on local context.

### 5. Altitude and permissiveness govern how much strategy you can sustain

Larson introduces **strategy altitude** — where a strategy is implemented (team, organisation, company) — and **permissiveness** — whether it mandates or advises ([When to write strategy, and how much?](https://lethain.com/when-write-down-engineering-strategy/), 2024-08-25).

*"Permissive strategies are less expensive than prescriptive strategies, because they require little-to-no enforcement. Lower-altitude strategies are less expensive than higher-altitude strategies."* The formula to increase strategy volume is to **reduce altitude or increase permissiveness, or both.**

His strongest advice in the whole body of work: *"If you take nothing else away from this chapter, try to always be working on exactly one strategy. Doing more feels like progress, but usually fails."* And: *"significantly more leaders fail by attempting too much strategy work than by attempting to do too little."*

### 6. The process, start to finish

Two processes exist for two different authorities.

**The staff-engineer path — write five, then synthesize** ([Write five, then synthesize](https://lethain.com/good-engineering-strategy-is-boring/)): *"To write an engineering strategy, write five design documents, and pull the similarities out."* Look for *"controversial decisions that came up in multiple designs, particularly those that were hard to agree on."* This works because design documents contain *"what bad strategies lack: detailed specifics grounded in reality."* The authority for the strategy comes from the precedent it documents.

**The executive path** ([Writing an engineering strategy](https://lethain.com/eng-strategies/)): write it yourself, don't delegate; pick a small working group for early feedback; write the diagnosis first and workshop it 1:1; then guiding policies; then share with the wider stakeholder set; then write the coherent actions; then spend time with the people most likely to disagree. Notably, Larson tells executives who feel unqualified: *"writing the strategy is one of the best learning opportunities you'll get."*

**Setting policy specifically** is six steps ([Setting policy for strategy](https://lethain.com/policy-for-strategy/)):

1. Review the diagnosis for obvious omissions.
2. Select policies that address it — **explicitly match each policy to the diagnosis it addresses**, and continue until every diagnosis is covered.
3. Consolidate overlapping policies.
4. **Backtest the policy against recent decisions you've actually made.**
5. Mine for conflict — seek out disagreeing perspectives.
6. Return to refinement if conviction is low.

Step 4 is the cheapest quality check available and requires no one else.

### 7. Writing advice that generalises

From [Write five, then synthesize](https://lethain.com/good-engineering-strategy-is-boring/):

- **Start where you are.** *"Waiting for missing information doesn't work: every missing document is missing for a good reason."*
- **Write the specifics.** *"Write until you start to generalize, and then stop writing … Specific statements create alignment; generic statements create the illusion of alignment."*
- **Be opinionated.** *"If they aren't opinionated, then they won't provide any clarity on decision making."*
- **Show your work.** *"Bad strategies state a policy without explanation, which decouples them from the context they were made. Without context, your strategy rapidly becomes incomprehensible."*
- **Gather widely, write alone.** *"Most folks are better writers than they are editors."*

### 8. What beginners get wrong

Collected failure modes, each attributable:

| Failure | Source |
|---|---|
| **Writing a vision instead of a strategy.** *"The reason most written strategies don't apply is because they're actually visions of how things could ideally work, rather than accurate descriptions of how things work today."* | [eng-strategies](https://lethain.com/eng-strategies/) |
| **Proclaiming axiomatic truths.** *"abandon your plan to proclaim axiomatic truths … lists of commandments are dead documents on arrival that cannot evolve with your organization."* | [things-that-arent-engineering-strategy](https://lethain.com/things-that-arent-engineering-strategy/) |
| **Mission statements.** *"Mission statements are an attempt to rewrite reality with force of desire, which is, I'm sad to say, folly."* | ibid. |
| **Generalising.** *"don't generalize" and "don't lie" are named as the rules of effective engineering strategy. | ibid. |
| **Skipping steps.** *"strategies fail more often due to avoidable errors than from fundamentally unsound thinking. Busy people skip steps. Especially steps they dislike or have failed at before."* | [components-of-eng-strategy](https://lethain.com/components-of-eng-strategy/) |
| **Policy without diagnosis.** *"Any strategy without a policy is useless, but you'll also find policies without context aren't worth much either."* | [policy-for-strategy](https://lethain.com/policy-for-strategy/) |
| **Missing operational mechanisms.** Stripe's rollout of agile *"struggled due to missing operational mechanisms"*; *"good policy loses to poor operational mechanisms every time."* | [is-this-strategy-any-good](https://lethain.com/is-this-strategy-any-good/) |
| **Structuring for the writer, not the reader.** *"The deliberate refusal to structure documents for readers is the root cause of a surprising number of good strategies that utterly fail to have their intended impact."* | [readable-engineering-strategy-documents](https://lethain.com/readable-engineering-strategy-documents/) |
| **Writing too much strategy at once.** Covered in Finding 5. | [when-write-down-engineering-strategy](https://lethain.com/when-write-down-engineering-strategy/) |
| **Strategy as procrastination.** *"Sometimes working on strategy is just snacking to avoid something more important."* | ibid. |

### 9. How to tell whether it is good

Larson rejects grading purely on outputs (you cannot separate the strategy's contribution from what would have happened anyway) and purely on inputs (a conceptually sound strategy that fails and is not revised is a failed strategy). His rubric has three parts ([Is this strategy any good?](https://lethain.com/is-this-strategy-any-good/)):

1. **How quickly is the strategy refined?** *"If a strategy starts out bad, but improves quickly, that's a better strategy than a mostly right strategy that never evolves."*
2. **How expensive is refinement for the teams involved?** *"Especially early on, good strategy is validated cheaply. Expensive strategies are discarded before they can be validated."*
3. **How well does the current iteration solve its diagnosis?** *"Strategy must eventually be graded on its impact."*

Strategies exist in **phases**, each beginning when new information renders the prior diagnosis incomplete. Abandoning a strategy is therefore often a sign of good strategy work, not failure.

A separate, practical readiness check: the "when to write" test. Larson describes three strategic states — globally consistent, consistent within teams, highly varied — and advises writing strategy when you are in the latter two, or trending toward them. Also: *"When you've rehashed the same discussion three or four times, it's time to write another strategy."*

## Recommendation

**For `#36`, and for the thirteen strategy documents behind it:**

**1. Adopt the five components as the thinking process and the inverted order as the published structure.** Write Explore → Diagnose → Refine → Policy → Operations; publish Policy → Operation → Refine → Diagnose → Explore, with a one-paragraph "Reading this document" preamble naming any refactors. This directly serves the Epic's requirement that an agent reach an answer from the document — agents, like Larson's "least motivated readers", need the policy first.

**2. Use the tradeoff test as the primary quality gate.** For every statement: what does it forbid, and what does it cost? Statements that forbid nothing are deleted. I expect this to cut a first draft substantially.

**3. Classify every policy as direction or guidance.** This is the practitioner form of the enforceable/advisory distinction the Epic requires, and it comes with a decision rule: direction when consistency matters more than judgment, guidance when the path depends on context you cannot anticipate. For agent-consumed rules, direction should be the default, with guidance used only where genuine judgment is required — and with escalation named when it is.

**4. Backtest against real decisions before publishing.** Seven programme decisions were made and recorded on 2026-09-19 (repository visibility, licence, schedule, milestone handling, strategy ordering, issue-raising scope, spike scheduling), plus the decisions to defer Tasks and Spikes to pickup. A draft strategy that cannot reproduce those decisions is not yet correct. **This also supplies the worked examples that `#36`'s acceptance criterion demands** — they already exist, and they are real rather than invented.

**5. Write the diagnosis honestly, not aspirationally.** The most common failure is writing a vision of how things should work. `docs/vision.md` already holds the aspiration; the strategy's diagnosis must describe the actual situation — one operator, no independent reviewer, no CI yet, agents that will infer whatever is unstated.

**6. Deviation: write more than one strategy, but drop the altitude.** Larson's advice is to work on exactly one strategy at a time, and that most failures come from attempting too much. Milestone 0 plans fourteen. I do not recommend abandoning M0, but the evidence says the plan carries real risk, and the mitigation is his own formula: **reduce altitude and increase permissiveness.** Prefer several small, permissive, low-altitude strategies with named escape hatches over one comprehensive prescriptive document. Sequence them, and require each to show impact on a real decision before starting the next.

## Confidence and Gaps

**Confidence: moderate-to-high on the anatomy, process and failure modes.** The sources converge, Larson's material is recent (2024–2025), published in full, and grounded in named worked examples from Stripe, Uber, Calm and Carta. Rumelt's kernel is the acknowledged foundation across all of them.

**Confidence: low on the solo-operator and agent-consumer adaptation.** Every source assumes an organisation: stakeholders, working groups, socialisation, consensus. Larson's process explicitly includes workshopping the diagnosis 1:1 and seeking external executive review. None of that is available here. Two specific mechanisms are lost and have no evidenced substitute:

- **Review by the people the strategy constrains.** This is the primary mechanism for catching a strategy that reads well and is unworkable. In this programme the constrained party is agents. Whether handing a draft to an agent and asking it to resolve a real Task constitutes an adequate substitute is **untested and is the obvious candidate for the next Spike.**
- **The five-design-docs input.** The staff-engineer path derives strategy from accumulated real decisions. This repository has almost no such precedent — which means the agentic delivery strategy is being written earlier in its evidence cycle than the literature recommends. The mitigation is to expect rapid refinement (rubric item 1) rather than accuracy on the first pass.

**Not established:** how to mark enforceable-versus-advisory such that the marking does not rot when enforcement changes; whether normative keyword conventions (RFC 2119) help or hinder agent readers; anything specific to machine-consumed policy documents. No source consulted addresses agents as document readers — this appears to be genuinely uncharted, and should be treated as invention rather than adoption.

## Consequences

If adopted:

- `#36` can be decomposed. The tasks follow the five components plus a publishing step, and the "worked examples" acceptance criterion is satisfied by the backtest against the seven recorded decisions.
- The strategy/contract split asserted in `#14` maps onto **policy versus operations**, which resolves the boundary question that has been open across `#36`, `#15`, `#16` and `#17` — the strategy carries diagnosis and policy; the contract carries operational mechanisms an agent executes.
- A template for programme strategy documents should be added under `docs/` once the first strategy proves the structure, rather than before.
- The M0 plan to produce fourteen strategy documents should be revisited against the altitude/permissiveness finding.

## Sources

| Source | Type | Consulted | Notes |
|---|---|---|---|
| [Steps to build an engineering strategy](https://lethain.com/components-of-eng-strategy/) — Will Larson | Book chapter, published free | 2026-09-19 | Published 2025-03-27. The five components. Chapter of *Crafting Engineering Strategy* (O'Reilly, Oct 2025) |
| [Writing an engineering strategy](https://lethain.com/eng-strategies/) — Will Larson | Book chapter | 2026-09-19 | Published 2023-02-13. Unedited chapter of *The Engineering Executive's Primer*. Rumelt's kernel, executive writing process, full example strategy |
| [Making engineering strategies more readable](https://lethain.com/readable-engineering-strategy-documents/) — Will Larson | Book chapter | 2026-09-19 | Published 2024-05-18. Inverted reading structure, strategy refactoring |
| [Setting policy for strategy](https://lethain.com/policy-for-strategy/) — Will Larson | Book chapter | 2026-09-19 | Published 2025-03-13. Four policy kinds, six-step policy process, backtesting |
| [Is this strategy any good?](https://lethain.com/is-this-strategy-any-good/) — Will Larson | Book chapter | 2026-09-19 | Published 2025-03-27. Three-part quality rubric, strategy phases |
| [When to write strategy, and how much?](https://lethain.com/when-write-down-engineering-strategy/) — Will Larson | Book chapter | 2026-09-19 | Published 2024-08-25. Strategic state, altitude, permissiveness, volume limits |
| [Write five, then synthesize](https://lethain.com/good-engineering-strategy-is-boring/) — Will Larson | Article | 2026-09-19 | Published 2020-11-26. Design-doc synthesis method, writing advice |
| [Things that aren't engineering strategy](https://lethain.com/things-that-arent-engineering-strategy/) — Will Larson | Article | 2026-09-19 | Published 2020-11-07. Exclusions: values, mission, axioms |
| [How should we control access to user data?](https://lethain.com/user-data-access-strategy/) — Will Larson | Worked example | 2026-09-19 | Published 2025-02-07. Full strategy in refactored inverted structure |
| [Strategy — thought pillar](https://rogerlmartin.com/thought-pillars/strategy) — Roger L. Martin | Author's own site | 2026-09-19 | "Strategy is choice"; the five-question Strategy Choice Cascade from *Playing to Win* (2013) |
| [craftingengstrategy.com](https://craftingengstrategy.com/) — Will Larson | Book site | 2026-09-19 | "strategy is the art of reproducibly making good decisions" |

Rumelt's *Good Strategy / Bad Strategy* (2011) is cited throughout as the origin of the diagnosis / guiding policy / coherent action kernel. It was not read directly for this research; the kernel is quoted here via Larson's engineering-specific application of it. The author's own site ([richardrumelt.com](https://www.richardrumelt.com/good-strategy-bad-strategy)) returned no readable content, and a McKinsey-hosted Rumelt article timed out. **Treat the kernel as reported secondhand** — it is uncontroversial and consistently quoted, but the primary text has not been verified here.
