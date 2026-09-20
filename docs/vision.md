# Vision

## The Goal

Create a secure, observable and governed agentic engineering platform where I can experiment, learn and build with emerging technologies, while AI agents autonomously plan, research, build, test and operate real software within clearly defined human controls.

The platform should make experimentation safe and repeatable, turn learning into reusable engineering capability, and make agentic software delivery reliable enough for real workloads — while preserving transparency, auditability and human decision-making.

## What This Is Proving

That a single engineer, working with AI agents, can run a real infrastructure programme end to end — and produce the evidence to show it.

Not that agents can write code. That is established. The claim is narrower and harder:

* that agent behaviour can be **governed by a written contract** rather than by whatever each model infers from a prompt
* that autonomy can be **bounded deliberately**, with the stop conditions stated in advance rather than discovered after an incident
* that the resulting delivery is **auditable** — every change traceable to a decision, and every decision to a recorded rationale
* that this holds up against **real infrastructure**, with real failure modes, rather than in a demonstration

## Why It Is Not Obvious

Four constraints make this a genuine engineering problem rather than a tooling exercise.

**Solo operator.** There is no independent reviewer. Approval gates are contractual, not enforced by a second pair of eyes, so the contract has to carry weight that process normally carries.

**Real hardware.** A single physical host with finite memory, one GPU, and no cluster to fail over to. Constraints are absolute, not negotiable.

**Public by default.** The work is visible while it is being done. Security posture has to be real, not retrofitted before publication.

**Agents do the delivery.** Not autocomplete — agents plan, research, implement, verify and hand off. The human decides and approves. An agent may land an approved change, but never decides that it should be landed.

## What Success Looks Like

* An agent, given only its issue and the linked contract, can determine whether it may start, whether it may decide, when it must stop, and what evidence it owes.
* Infrastructure is reconstructible from the repositories. A total loss of the host is an inconvenience, not an incident.
* Every merged change traces to a decision, and every significant decision traces to a recorded rationale.
* Security and exposure claims are verified by tests rather than asserted by configuration review.
* The platform runs workloads worth running, on hardware that is actually in the house.
* Learning compounds — each experiment leaves behind reusable capability rather than a one-off result.

## What This Is Not

**Not a product.** Nothing here is built for other people to deploy.

**Not a distribution or framework.** The configuration is specific to one homelab. It is published because it is useful to read, not because it generalises.

**Not a demonstration.** The platform is intended to run real workloads and to be operated, not staged.

**Not fully autonomous.** Agents act within stated boundaries. Destructive and trust-affecting actions require human approval. An agent may land a change only where an independent review exists and the human has approved that specific merge; the authority is delegated per merge, never standing, and the human retains it. That is a deliberate design position, not a limitation awaiting removal.

## How This Document Is Used

This is the reference point for scope decisions. Work that does not serve the goal above is out of scope, however interesting it is. Where a decision record, strategy or acceptance criterion needs a reason, the reason is traced back here.

Architecture is documented under [`architecture/`](architecture/). Decisions and their rationale are recorded under [`adr/`](adr/). Programme execution is tracked in GitHub Issues and Projects.
