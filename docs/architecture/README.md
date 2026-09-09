# Architecture

This directory contains architecture documentation that describes the current design of the ClankerOps Homelab as a system.

Architecture documentation should explain how the system is structured, how major components interact, where important boundaries exist, and how the overall platform is intended to operate.

## Purpose

The documentation in this directory should help a reader understand:

* what the homelab platform is
* the major systems and components that make it up
* how those components interact
* environment and deployment boundaries
* network and trust boundaries
* important data and control flows
* shared platform capabilities
* significant architectural constraints

The intended audience includes engineers, technical reviewers, future maintainers, AI agents, and anyone evaluating the project as part of the ClankerOps portfolio.

## Scope

This directory is for system-level and cross-repository architecture.

Implementation details that belong entirely to a single component should normally live with that component's repository.

Examples of appropriate content include:

* system context
* platform architecture
* environment architecture
* deployment architecture
* security architecture
* networking
* observability architecture
* identity and access flows
* cross-repository dependencies

## Current Architecture

The architecture documented here represents the current intended design unless superseded by a newer document or an accepted Architectural Decision Record.

Architecture documentation should describe the system as it exists or is intentionally being built, rather than preserving every historical design that has previously been considered.

Historical reasoning and significant design choices belong in the ADR collection.

## Architectural Decisions

Significant decisions that affect the architecture should be recorded under:

[`../adr/`](../adr/)

Architecture documents may reference ADRs when explaining why a particular design exists.

## Diagrams

Diagrams should be stored alongside the architecture documentation they support or within an appropriate diagrams directory.

Where practical, diagrams should use source-controlled text formats so they can be reviewed, versioned, and maintained with the rest of the repository.
