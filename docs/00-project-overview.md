# Experimental Lab — Project Overview

## Purpose

Experimental Lab is a local AI agent laboratory designed to build, test and evolve autonomous and semi-autonomous agents running on local infrastructure.

The initial objective is to deliver a Minimum Viable Product (MVP) that allows the user to interact remotely with an AI agent running on a local Ubuntu system.

The agent must be able to receive instructions through a messaging interface, perform explicitly authorized tasks on the local computer, and return results through the same communication channel.

The project is designed as a foundation for future development of specialized local agents for software development, infrastructure, cloud operations, automation and technical analysis.

---

# Vision

Build a modular, reproducible and production-oriented local AI agent platform.

The platform will initially focus on a single local agent capable of performing practical tasks on an Ubuntu system within explicitly defined authorization and security boundaries.

Future milestones may expand the platform into a system of specialized agents capable of working with software projects, infrastructure and cloud environments.

---

# Mission

Design and maintain a local AI infrastructure where services can be deployed, upgraded and removed independently using containerized technologies where appropriate.

The architecture must follow the actual requirements of the MVP.

Every important architectural decision must be documented and justified before implementation.

Every deployment should be reproducible from source control.

---

# MVP Definition

The MVP is a remotely accessible AI agent running in the user's local Ubuntu environment.

The user communicates with the agent through a messaging platform.

The initial preferred communication channel is Telegram.

The agent receives instructions remotely, evaluates the requested task, performs authorized operations within defined boundaries and returns the result through the messaging channel.

The core MVP interaction model is:

```text
Remote User
     │
     │ Remote message
     ▼
Messaging Platform
     │
     ▼
Local AI Agent
     │
     ├── Authorized Workspace Operations
     │
     └── Authorized Local Ubuntu Operations
```

The primary purpose of the MVP is to allow the user to interact remotely with the local environment through a controlled AI agent.

Docker is an implementation and deployment mechanism for services that require containerization. Docker infrastructure is not an independent product objective and must follow the actual component, communication, persistence and security requirements of the MVP.

---

# MVP Capabilities

## Workspace Operations

The agent must be able to perform authorized operations within a defined local workspace.

These operations may include:

- Creating directories.
- Creating files.
- Modifying files.
- Deleting files when explicitly required and authorized.
- Creating complete project structures.
- Generating configuration files.
- Creating README files.
- Creating `.gitignore` files.
- Creating Docker configurations.
- Organizing project documentation.
- Working with projects located inside the authorized workspace.

The workspace boundary, access permissions and enforcement mechanism must be defined before implementation.

The agent must not receive unrestricted file-system access merely for convenience.

## Git Operations

The agent should be able to assist with Git operations inside authorized projects.

These operations may include:

- Inspecting repository status.
- Initializing repositories.
- Creating branches.
- Reviewing changes.
- Adding files to the staging area.
- Preparing commits.
- Creating commits.

Remote publishing and push authorization must be handled separately and explicitly.

## Local Ubuntu Operations

The agent must be capable of assisting with the local Ubuntu environment within a defined authorization model.

This may include:

- Diagnosing system problems.
- Inspecting logs.
- Checking service status.
- Inspecting system configuration.
- Reviewing package status.
- Checking available updates.
- Updating packages when explicitly authorized.
- Installing required packages when explicitly authorized.
- Diagnosing Docker problems.
- Diagnosing development environment problems.
- Assisting with selected local security tasks.

System-level operations are not equivalent to normal workspace operations.

The execution model, authorization requirements and privileged-operation policy must be defined before implementation.

---

# Scope

The laboratory currently focuses on:

- AI agents.
- AI coding agents.
- Local AI agent experimentation.
- Local Large Language Models (LLMs).
- Docker-based infrastructure where required.
- Local orchestration.
- Remote interaction with local agents.
- Controlled local execution.
- Documentation.
- Architecture.

Future versions may include:

- Monitoring.
- Observability.
- CI/CD.
- Kubernetes.
- Distributed AI workloads.
- Multi-node deployments.
- Specialized AI agents.
- Cloud infrastructure analysis.
- FinOps and cost optimization.

---

# Architecture and Design Principles

## Requirements Before Infrastructure

Infrastructure must follow actual component requirements.

Before implementing Docker services, networks, volumes or exposed ports, the project must identify:

- The agent runtime.
- The messaging integration model.
- The communication paths between components.
- The workspace boundary.
- The host execution model.
- The privileged-operation policy.
- Secret requirements.
- Persistence requirements.
- Required networking.
- Service boundaries.

Unnecessary infrastructure must not be created in anticipation of hypothetical services.

## Modularity

Every service should remain independently deployable, upgradeable and removable.

## Reproducibility

Every deployment must be reproducible from source control.

A new workstation should be capable of rebuilding the laboratory using the project repository and documented requirements.

## Documentation First

Every important decision must be documented before implementation.

Documentation is part of the project and is the primary source of truth for project state, roadmap and architectural decisions.

## Infrastructure as Code

Infrastructure configuration should be stored as code whenever possible.

Manual configuration should be minimized.

## Incremental Evolution

The laboratory is expected to grow over time.

The MVP should provide a practical foundation without introducing unnecessary complexity before requirements justify it.

## Host Integrity

The Ubuntu host operating system should remain as clean as possible.

Application dependencies should belong inside containers where appropriate.

Host-level access required by the agent must be explicitly designed and controlled.

## Controlled Local Execution

The agent must operate within defined and authorized boundaries.

Project and file operations should be restricted to an authorized workspace.

System-level operations must follow a defined permission and authorization model.

The agent must not have unrestricted access to the local system without an explicit architectural decision.

Docker container isolation alone does not automatically solve host-access control requirements.

Any host mounts, Docker socket access, privileged containers or sudo access require explicit architectural review.

---

# High-Level Target Architecture

The target architecture begins with a remote communication channel connected to a local AI agent.

The agent performs authorized operations through explicitly defined execution boundaries.

```text
                 Remote User
                      │
                      │ Messaging
                      ▼
             Messaging Platform
                      │
                      ▼
              Local Ubuntu Host
                      │
                      ▼
                Local AI Agent
                 /            \
                /              \
               ▼                ▼
      Authorized Workspace   Authorized System Operations
             │                    │
             ▼                    ▼
          Projects             Ubuntu
          Files                Services
          Git                  Packages
          Docker               Logs
```

Containerized services may be introduced where they support this architecture.

Additional services must be justified by a defined requirement.

Potential services include:

- Claw Code or another validated agent runtime.
- Ollama.
- Open WebUI.
- PostgreSQL.
- Redis.

The inclusion and role of each service must be defined by the relevant milestone before implementation.

---

# Architecture Definition Sequence

The project follows this sequence:

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
    ↓
Document and commit
```

No infrastructure component should be implemented solely because it appears in a future technology list.

---

# Repository Organization

The repository separates architecture decisions, documentation and future infrastructure or application services.

The exact repository structure must be inspected before implementation.

Existing directories should not be recreated blindly.

Repository documentation is authoritative when it conflicts with reconstructed or historical context.

---

# Initial Roadmap Logic

## Milestone 1 — Foundation

Completed.

The technical and documentation foundation was established.

## Milestone 2 — MVP Architecture and Security Boundary

Current milestone.

Define the minimum architecture required for the remote local AI agent MVP before infrastructure implementation begins.

## Milestone 3 — Docker Platform Implementation

Design and implement only the Docker infrastructure required by the validated MVP architecture.

## Milestone 4 — First AI Agent

Deploy and validate the first AI agent runtime.

## Milestone 5 — Remote Interaction

Integrate the selected messaging platform and validate remote-to-local task execution.

## Milestone 6 — Local AI Platform and Future Services

Introduce additional AI models and supporting services when justified by requirements.

Future specialized agents may evolve from this foundation.

---

# MVP Success Criteria

The MVP will be considered successful when the following workflow is functional:

1. The user can send an instruction remotely through the selected messaging platform.
2. The local agent receives the instruction.
3. The agent interprets the requested task.
4. The agent verifies that the requested operation is permitted.
5. The agent performs the authorized operation within the defined boundary.
6. The agent can create or modify projects within the authorized workspace.
7. The agent can perform defined Git operations within authorized projects.
8. The agent can assist with defined Ubuntu diagnostic and administration tasks.
9. Privileged operations require the defined additional authorization.
10. The agent reports the task result back through the messaging platform.

---

# Out of Scope for the Initial MVP

The following are not required unless they become necessary for the defined core workflow:

- Multi-agent orchestration.
- Distributed agent systems.
- Kubernetes.
- Multi-node deployments.
- PostgreSQL as a mandatory component.
- Redis as a mandatory component.
- Open WebUI as the primary user interface.
- Cloud infrastructure management.
- FinOps analysis.
- Advanced cloud cost optimization.
- Unrestricted autonomous system administration.

---

# Project Status

Current Milestone:

Milestone 2 — MVP Architecture and Security Boundary

Current Objective:

Define and validate the minimum component architecture and security boundaries required for the remotely accessible local AI agent MVP.

No implementation work for the Docker platform should begin until the required component model and authorization boundaries have been sufficiently defined.
