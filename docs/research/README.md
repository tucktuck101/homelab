# Research

This directory holds the durable output of research work — the evidence gathered while reducing uncertainty, and the recommendation that evidence supports.

Research is normally commissioned by a **Spike**. The Spike issue carries the question, the timebox and the audit trail; the document here carries the findings, so that knowledge survives the issue being closed.

## What Belongs Here

* Comparisons of options, with the criteria used and the evidence behind each
* Investigations into unfamiliar problem areas
* Feasibility findings, measurements and prototype results
* Surveys of current practice, where the result informs a decision

## What Does Not Belong Here

| Content | Belongs in |
|---|---|
| A decision and its consequences | [`../adr/`](../adr/) |
| How the system is built and behaves | [`../architecture/`](../architecture/) |
| What the programme is for | [`../vision.md`](../vision.md) |
| Rules that govern how work is done | The relevant strategy document |
| Progress, status or discussion | The issue |

Research records **what was found**. An ADR records **what was decided**. A research document may recommend a decision, but recording that decision is a separate act — and if the decision is significant, it gets its own ADR that cites this research.

## Naming

```text
docs/research/<issue-number>-<short-slug>.md
```

Zero-padded to four digits, using the number of the Spike or issue that commissioned the work — for example `0057-strategy-document-form.md`. The prefix makes the link back to the commissioning issue mechanical rather than a matter of memory.

Research not commissioned by an issue uses `0000-` and states in the document why no issue exists.

## Writing One

Start from [`TEMPLATE.md`](TEMPLATE.md).

Three properties matter more than length:

**Sourced.** Every claim that is not the author's own reasoning cites where it came from, with the date it was consulted. Primary sources are preferred over summaries of them.

**Bounded.** State what was *not* investigated. An unstated boundary reads as an absence of evidence rather than a deliberate exclusion.

**Conclusive.** End with a recommendation and the reasoning for it. A document that surveys options without recommending one has not finished the job the Spike asked for.

## Status and Supersession

Research is a record of what was known at a point in time. It is **not** revised as the world changes.

If later work overturns a finding, write a new document and mark the old one superseded in its front matter, linking forward. The original stays in place — an audit trail that is edited to stay correct is not an audit trail.

## Convention Status

**Provisional.** This convention was established while resolving the first Spike that needed somewhere to put its findings. The programme's documentation and knowledge strategy will either adopt it or replace it; until then, this is the standard.
