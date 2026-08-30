# Experimental Lab — Project State

## Project Information

Project:
Experimental Lab

Status:
🟢 Active

Current Milestone:
🟡 Milestone 2 — MVP Architecture and Security Boundary

Previous Milestone:
✅ Milestone 1 — Foundation

---

# Current Objective

Define and validate the minimum architecture required to implement the remotely accessible local AI agent MVP before infrastructure implementation begins.

The MVP is:

- reactive;
- single-user;
- controlled through Telegram;
- based on Claw Code as the Agent Runtime;
- bounded by an authorized workspace;
- capability-aware;
- deny-by-default;
- able to manage authorized Docker workloads;
- able to perform a limited set of system package update operations.

---

# Decisions Already Defined

## Interaction

```text
User
  ↓
Telegram
  ↓
Claw Code Agent Runtime
  ↓
Capabilities
  ↓
Workspace / Git / Docker / Limited System Updates
  ↓
Result
  ↓
Telegram
  ↓
User
```

The agent is reactive and does not initiate autonomous tasks.

The agent may ask follow-up questions before executing a task.

## Identity

The MVP is single-user.

The authorized Telegram user/chat identity is used for authorization.

OAuth is not required for the initial MVP.

Local Wi-Fi is not considered an authentication mechanism.

The preferred Telegram communication model uses outbound communication from the local environment and avoids publicly exposing the agent.

## Workspace

The workspace is the primary filesystem boundary.

The agent may operate inside the authorized workspace.

Arbitrary host filesystem access is denied.

## Capabilities

The system follows a deny-by-default model.

If an operation is not explicitly available as an authorized capability, it must not execute.

Capabilities should preferably be exposed through structured tools rather than arbitrary shell strings.

## Capability Escalation

When the agent needs an unavailable capability, it must request authorization rather than bypassing the policy.

The request must explain:

- required capability;
- resource;
- reason;
- objective;
- risk;
- available alternatives.

The agent cannot grant capabilities to itself.

The initial approval scope should be as narrow as practical, preferably one operation.

## Docker

Docker is an MVP capability.

The agent may manage Docker workloads associated with the authorized workspace.

The following are denied:

```text
Host filesystem mounts
--privileged
--pid=host
--network=host
--device
Arbitrary host bind mounts
Arbitrary Linux capabilities
```

The workspace may be mounted into workloads when explicitly authorized.

## Git

Git is required for the development and recovery workflow:

```text
Investigate
  ↓
Compare versions
  ↓
Modify
  ↓
Test
  ↓
Commit
  ↓
Synchronize repository
```

Initial Git capabilities include read, modification and synchronization operations as defined in the Milestone 2 document.

Remote publishing (`push`) requires an explicit decision before becoming a normal capability.

## System Updates

Initial system capabilities are limited to:

```text
apt list --upgradable
apt update
apt upgrade
```

General system administration is outside the initial MVP.

---

# Claw Code Baseline

Claw Code is the Agent Runtime.

The project will standardize against the current `main` branch of:

`ultraworkers/claw-code`

The exact version and commit used for implementation must be recorded.

Before implementation:

1. Build the current baseline.
2. Run `claw doctor`.
3. Run `claw version`.
4. Inspect MCP configuration and registration.
5. Validate the permission system.
6. Validate `allowedTools`.
7. Validate `allow`, `deny` and `ask`.
8. Validate workspace restrictions.
9. Validate MCP discovery and invocation.

---

# MCP Direction

MCP is the preferred mechanism for exposing capabilities that Claw does not already provide adequately.

The intended architecture is:

```text
Telegram
    ↓
Telegram Adapter
    ↓
Claw Code
    ↓
MCP
    ↓
Experimental Lab Capability Server
    ├── Docker
    └── System
```

MCP provides the structured tool interface.

The capability server must validate requests before execution.

Schema validation alone is not considered sufficient security.

The first custom server is expected to be:

`experimental-lab-docker-mcp`

---

# Current Milestone 2 Tasks

- [ ] MVP Component Map.
- [ ] Identify and record the exact Claw Code version and commit.
- [ ] Build and validate Claw.
- [ ] Run `claw doctor`.
- [ ] Run `claw version`.
- [ ] Inspect Claw MCP configuration and registration.
- [ ] Validate Claw permission behavior.
- [ ] Validate `allowedTools`.
- [ ] Validate `allow`, `deny` and `ask`.
- [ ] Validate workspace restrictions.
- [ ] Perform minimal MCP integration spike.
- [ ] Map Claw native capabilities against MVP capabilities.
- [ ] Define Docker capability schemas and parameter restrictions.
- [ ] Define Git capability policy.
- [ ] Define system-update capability policy.
- [ ] Define capability escalation flow.
- [ ] Design `experimental-lab-docker-mcp`.
- [ ] Define Telegram adapter.
- [ ] Define secret handling.
- [ ] Define persistence requirements.
- [ ] Define networking requirements.
- [ ] Review existing ADRs and create/update ADRs when required.
- [ ] Produce the minimum implementation architecture for Milestone 3.

---

# Immediate Next Step

The next technical task is:

## Claw + MCP Integration Spike

Do not build the complete Docker MCP server yet.

First prove:

```text
Claw
  ↓
MCP Server
  ↓
Test Tool
  ↓
Result
```

Then verify:

- tool registration;
- tool discovery;
- tool schema;
- `allowedTools`;
- permission behavior;
- denial behavior;
- invocation from the agent.

Only after this is validated should the Docker MCP capability server be implemented.

---

# Milestone 2 Definition of Done

Milestone 2 is complete when:

1. MVP interaction flow is documented.
2. Claw baseline is reproducible.
3. Claw MCP integration has been demonstrated.
4. Claw tools and permission controls have been mapped.
5. MVP capabilities are explicitly defined.
6. Unlisted capabilities are denied by default.
7. Docker operations are exposed through structured capabilities.
8. Arbitrary host filesystem access is denied.
9. Privileged Docker configuration is denied.
10. Capability escalation requires explicit user authorization.
11. Telegram identity authorization is defined.
12. Secrets, persistence and networking requirements are documented.
13. Minimum implementation architecture is documented.
14. Milestone 3 can begin without unresolved architectural assumptions.

---

# Session Procedure

At the beginning of each session:

1. Read `docs/project-state.md`.
2. Read `docs/Roadmap.md` when planning is involved.
3. Read relevant ADRs for architectural decisions.
4. Inspect the repository when current state is uncertain.
5. Confirm the current milestone and objective.
6. Continue from the next unfinished task.

At the end of each session:

1. Update `docs/project-state.md`.
2. Update `docs/Roadmap.md` when planning or status changes.
3. Update ADRs when architectural decisions are made.
4. Commit completed work.
5. Record the next starting point.

---

# Source-of-Truth Hierarchy

1. Current repository documentation.
2. Current repository contents.
3. Current active conversation.
4. Historical handoff/context.

Historical material provides continuity but does not override the current repository state.
