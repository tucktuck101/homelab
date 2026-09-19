# ClankerOps Homelab

ClankerOps Homelab is the public umbrella repository for my self-hosted infrastructure, platform engineering, DevSecOps, and related portfolio work.

This repository exists to provide a stable entry point into the wider homelab ecosystem. It contains the cross-cutting architecture, engineering principles, project documentation, decision records, roadmap, and links to the repositories that implement individual parts of the platform.

## What Lives Here

* Overall system architecture
* Cross-repository design decisions
* Security and operational principles
* Project roadmap and planning
* Portfolio documentation
* Links to component repositories and live services

Implementation details that belong to a specific platform component are kept in that component's own repository.

## Repository Structure

```text
docs/
├── vision.md       Programme goal, claim and scope boundary
├── architecture/   System-level architecture and design
└── adr/            Cross-cutting Architectural Decision Records
```

Additional areas will be added as the project grows.

## Sources of Truth

The goal of the programme and what it is intended to prove are stated in [`docs/vision.md`](docs/vision.md).

The current architecture is documented under [`docs/architecture/`](docs/architecture/).

Architectural decisions and their rationale are recorded under [`docs/adr/`](docs/adr/).

GitHub Projects and Issues are used to track planned and active work.

## Contribution Policy

This is a personal engineering and portfolio project. External code contributions are not currently accepted.

Issue reports, security disclosures, and feedback may be accepted where appropriate.
