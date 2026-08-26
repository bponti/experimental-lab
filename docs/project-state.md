# Experimental Lab — Project State

## Project Information

Project:

Experimental Lab

Status:

🟢 Active

Last Updated:

2026-08-26

---

# Current Progress

Last Completed Milestone:

✅ Milestone 1 — Foundation

Current Milestone:

🟡 Milestone 2 — MVP Architecture and Security Boundary

Status:

In Progress

---

# Last Completed

Milestone:

Milestone 1 — Foundation

Last Completed Deliverable:

Phase 0 — Environment Audit

Completion Status:

Completed

Deliverables Completed:

- Git repository initialized.
- Documentation standards established.
- README completed.
- Project Overview established.
- ADR-0001 approved.
- ADR-0002 approved.
- Phase 0 Environment Audit completed.
- Documentation reviewed.
- Repository published.
- Milestone 1 exit criteria satisfied.

Historical commit information must be revalidated against the current repository when needed.

---

# Current Objective

Define and validate the minimum architecture required to implement the remotely accessible local AI agent MVP.

Before Docker infrastructure implementation begins, the project must identify the actual components, communication paths, execution boundaries and authorization requirements that the MVP requires.

Infrastructure must follow requirements rather than assumptions about future services.

---

# Current Tasks

- [ ] Confirm the current MVP interaction flow.
- [ ] Map the minimum required MVP components.
- [ ] Evaluate and define the first AI agent runtime requirements.
- [ ] Determine how the messaging platform communicates with the local agent.
- [ ] Define the authorized workspace boundary.
- [ ] Define workspace read and write permissions.
- [ ] Define the local command execution model.
- [ ] Define the distinction between normal and privileged operations.
- [ ] Define the privileged-operation authorization policy.
- [ ] Define the Docker socket access policy.
- [ ] Define host mount requirements.
- [ ] Define secret-handling requirements.
- [ ] Define persistent-data requirements.
- [ ] Define actual networking and communication requirements.
- [ ] Define the minimum service boundaries.
- [ ] Review existing ADRs for alignment with the updated architecture.
- [ ] Create or update ADRs for new architectural decisions where required.
- [ ] Prepare the minimum Docker implementation plan.

---

# Immediate Next Deliverable

Milestone 2 — MVP Architecture and Security Boundary

Minimum Architecture Definition

Expected outcome:

A documented answer to what the MVP actually requires before Docker services, networks, volumes, ports or privileged access are implemented.

---

# Current Architectural Principle

The project follows this execution order:

```text
Define MVP
    ↓
Identify required components
    ↓
Define communication paths
    ↓
Define security and authorization boundaries
    ↓
Design minimum architecture
    ↓
Implement required infrastructure
    ↓
Deploy agent services
    ↓
Integrate remote messaging
    ↓
Validate authorized task execution
```

No implementation work should bypass the architecture and security definition stage.

---

# Active ADRs

- ADR-0001.
- ADR-0002.

Existing ADRs must be reviewed before assuming that new architectural decisions are required.

New ADRs should be created only when a significant decision has been defined.

---

# Repository

Platform:

GitHub

Repository:

bponti/experimental-lab

Default Branch:

main

Repository Status:

Operational

Working Tree:

Must be checked against the local repository at the beginning of an implementation session.

---

# Current Synchronization State

State A — Documentation

Confidence:

Very High

Source:

- Current Project State.
- Current Roadmap.
- Current Project Overview.
- Relevant ADRs.
- Current repository contents.

Historical handoff material provides continuity but does not override current repository documentation.

---

# Blockers

None currently identified.

The main pending architectural work is intentional: the minimum MVP architecture and its security boundary must be defined before infrastructure implementation.

---

# Session Start Procedure

At the beginning of every work session:

1. Review `docs/project-state.md`.
2. Review `docs/Roadmap.md` when planning or project direction is involved.
3. Review relevant ADRs when an architectural decision is involved.
4. Inspect the repository when documentation conflicts with historical context.
5. Confirm the current milestone.
6. Confirm the current objective.
7. Identify the next planned task.
8. Declare the information source state.

No implementation work begins until the current project state has been confirmed.

---

# Session End Procedure

Before ending a work session:

1. Update `docs/project-state.md`.
2. Update `docs/Roadmap.md` if milestone status or planning changed.
3. Update ADRs if architectural decisions were made.
4. Commit completed work.
5. Define the starting point for the next session.

---

# Information Confidence Model

## State A — Documentation

Source:

- `docs/project-state.md`
- `docs/Roadmap.md`
- ADRs
- Other relevant repository documentation

Confidence:

Very High

Use when current project documentation has been reviewed.

## State B — Active Conversation

Source:

Current conversation.

Confidence:

High

Use when the required information exists entirely within the active conversation.

## State C — Reconstruction

Source:

Partial context or reconstructed memory.

Confidence:

Medium

Important planning, milestone and architectural conclusions must be verified against current repository documentation before implementation.

---

# Documentation Rule

The repository documentation is the primary source of truth for the project.

When discussing milestones, deliverables, roadmap planning or project direction:

- `docs/project-state.md` defines the current operational state.
- `docs/Roadmap.md` defines the planned evolution.
- ADRs document significant architectural decisions.
- The active conversation provides short-term execution context.
- Historical handoff material provides continuity.
- Reconstructed memory is the lowest-confidence source.

If documentation conflicts with historical context, inspect the current repository and follow the documented project state.
