# Milestone 2 — MVP Architecture and Security Boundary

## Goal

Define and validate the minimum architecture required to implement the Experimental Lab MVP before building infrastructure.

The MVP is a reactive, single-user local AI agent controlled through Telegram. The agent operates within an authorized workspace and exposes controlled capabilities for workspace, Git, Docker and limited system-package operations.

Infrastructure must follow validated requirements. No unnecessary Docker services or security mechanisms should be introduced before they are justified.

## MVP Definition

```text
User
  ↓
Telegram
  ↓
Claw Code Agent Runtime
  ↓
Capability / Permission Layer
  ↓
Authorized Workspace
  ├── Files
  ├── Git
  └── Docker Workloads
         ├── Build
         ├── Run / Deploy
         ├── Start
         ├── Stop
         ├── Restart
         ├── Remove
         ├── Inspect
         ├── Logs
         ├── Stats
         ├── Exec
         └── Resource Update
  ↓
Result
  ↓
Telegram
  ↓
User
```

The agent is reactive. It remains available to receive requests but does not initiate autonomous tasks.

The agent may ask follow-up questions when information is missing. Execution occurs only after the required information is available and the operation is authorized.

## Identity and Access

- MVP is single-user.
- Only the authorized Telegram identity may interact with the agent.
- Authorization is based on Telegram user/chat identity.
- OAuth is not required for the MVP.
- Local Wi-Fi is not considered an authentication mechanism.
- Preferred Telegram communication uses outbound connections from the local environment.
- No publicly exposed inbound agent service is required initially.

## Claw Code Baseline

Claw Code is the Agent Runtime.

The project will standardize against the current `main` branch of `ultraworkers/claw-code`.

The exact commit used as the implementation baseline must be recorded.

Before implementation:

1. Build the current Claw Code baseline.
2. Run `claw doctor`.
3. Run `claw version`.
4. Inspect MCP configuration and registration interfaces.
5. Verify the permission system.
6. Verify `allowedTools`.
7. Verify `allow`, `deny` and `ask` behavior.
8. Verify workspace restrictions.
9. Verify MCP tool discovery and invocation.

## Capability Model

The MVP follows a deny-by-default model.

The agent may only perform operations explicitly exposed and authorized by configuration.

Capabilities should preferably be exposed as structured tools rather than arbitrary Bash strings.

```text
Agent
  ↓
Capability Request
  ↓
Schema Validation
  ↓
Policy Validation
  ↓
Executor
  ↓
Target Resource
```

## Capability Escalation

If the agent requires an operation outside the current policy, it must not execute it automatically.

It must explain:

- required capability;
- requested resource;
- reason;
- objective;
- risk;
- available alternatives.

The user may deny, approve once, approve temporarily, or later add the capability permanently.

The agent must never grant capabilities to itself.

Initial approval should default to the narrowest useful scope, preferably one operation.

## Workspace Boundary

The workspace is the primary filesystem boundary.

```text
Ubuntu Host
│
├── /workspace
│    ├── project-a
│    ├── project-b
│    └── ...
│
└── Other host filesystem
     └── Denied by default
```

The agent may read and modify files inside the authorized workspace.

Arbitrary host filesystem access is denied.

## Docker Boundary

Docker is an MVP capability.

The agent may manage workloads associated with the authorized workspace.

The Docker capability must not provide arbitrary host access.

Host access restrictions:

```text
DENY
├── Host filesystem mounts
├── --privileged
├── --pid=host
├── --network=host
├── --device
├── Arbitrary host bind mounts
└── Arbitrary Linux capabilities
```

The workspace may be mounted into a workload when explicitly authorized as part of the project.

## Initial Docker Capabilities

Candidate capabilities:

```text
docker_list
docker_build
docker_run
docker_create
docker_start
docker_stop
docker_restart
docker_remove
docker_logs
docker_inspect
docker_stats
docker_exec
docker_update
docker_image_list
docker_image_pull
docker_image_remove
docker_compose_build
docker_compose_up
docker_compose_down
docker_compose_restart
docker_compose_ps
docker_compose_logs
```

Each capability must define:

- input schema;
- permitted resources;
- permitted arguments;
- permitted resource ranges;
- privilege level;
- approval requirement.

## Docker Exec

`docker_exec` requires special restriction.

The MVP must not turn it into unrestricted arbitrary shell access inside workloads without an explicit decision.

The initial implementation should expose only the minimum diagnostic or operational commands required by the MVP.

## Git Capability

Git supports the development and recovery workflow:

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

Initial capabilities:

```text
status
log
diff
show
branch
switch
checkout
add
restore
commit
fetch
pull
merge
rebase
remote
tag
```

Remote publishing (`push`) requires an explicit decision before becoming a normal capability.

## System Update Capability

Initial system capability:

```text
apt list --upgradable
apt update
apt upgrade
```

General system administration is outside the initial MVP.

## MCP Architecture

MCP is the preferred mechanism for exposing capabilities not already adequately provided by Claw.

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

The capability server remains responsible for validating requests before execution.

Schema validation alone is not considered sufficient security.

## Docker MCP Server

The first custom MCP server should be:

```text
experimental-lab-docker-mcp
```

Its purpose is to expose only the Docker operations required by the MVP.

It must not expose a generic Docker shell.

It must not expose arbitrary host mounts or privileged Docker configuration.

The server should use a structured Docker API/SDK rather than arbitrary shell commands where practical.

## Telegram Adapter

The Telegram adapter is responsible for:

- receiving messages;
- identifying the authorized Telegram user;
- forwarding requests to Claw;
- returning Claw responses;
- supporting multi-turn conversations;
- forwarding capability-approval requests.

It must not become an unrestricted execution layer.

## Secrets

The MVP must define secure handling for:

- Telegram bot token;
- Git credentials if required;
- future API credentials.

Secrets must not be embedded in prompts, source code or committed configuration.

## Persistence

Evaluate which state must survive restarts:

- Claw configuration;
- capability policy;
- conversation/session state;
- workspace data;
- Docker state;
- credentials;
- logs.

No database should be introduced unless requirements justify it.

## Networking

Required communication paths must be documented:

```text
Agent → Telegram
Agent → MCP
MCP → Docker Engine
Agent → Workspace
```

Any additional network path requires a documented purpose.

## Deliverables

- [ ] MVP Component Map.
- [ ] Current Claw Code baseline identified by version and commit.
- [ ] Claw MCP integration spike.
- [ ] Claw permission-system validation.
- [ ] Claw `allowedTools` validation.
- [ ] Workspace boundary definition.
- [ ] Capability model definition.
- [ ] Capability escalation flow.
- [ ] Docker capability policy.
- [ ] Git capability policy.
- [ ] System-update capability policy.
- [ ] Docker MCP server design.
- [ ] Telegram adapter design.
- [ ] Secret-handling decision.
- [ ] Persistence decision.
- [ ] Network requirements.
- [ ] Required ADR updates/new ADRs.

## Definition of Done

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

## Exit Architecture

```text
                         Telegram
                            │
                            ▼
                    Telegram Adapter
                            │
                            ▼
                    ┌──────────────┐
                    │   Claw Code  │
                    │ Agent Runtime│
                    └───────┬──────┘
                            │
                         MCP Tools
                            │
                 ┌──────────┴──────────┐
                 │                     │
                 ▼                     ▼
        Docker Capability       System Capability
              Server                  Server
                 │                     │
                 ▼                     ▼
          Docker Engine             Ubuntu
                 │
                 ▼
       Authorized Workspace
          Docker Workloads
```

Milestone 3 begins only after this architecture has been validated.
