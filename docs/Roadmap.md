# Experimental Lab Roadmap

## Purpose

This roadmap defines the planned evolution of Experimental Lab.

Each milestone represents a stable engineering stage.

A milestone is completed only after its documented deliverables and exit criteria have been satisfied.

The roadmap follows the architecture-first principle: infrastructure is implemented only after the requirements and boundaries it must support have been defined.

---

# Project Vision

Build a modular, reproducible and production-oriented local AI agent platform.

The initial product is a remotely accessible AI agent operating within controlled boundaries on a local Ubuntu environment.

---

# Current Status

Current Milestone:

🟡 Milestone 2 — MVP Architecture and Security Boundary

Previous Milestone:

✅ Milestone 1 — Foundation

---

# Milestone 1 — Foundation

## Goal

Establish the initial technical, documentation and architectural foundations of the laboratory.

## Deliverables

- Git repository.
- Documentation standards.
- README.
- Project Overview.
- ADR-0001.
- ADR-0002.
- Phase 0 environment audit.
- Repository publication.

## Exit Criteria

- Documentation approved.
- Repository initialized.
- Phase 0 audit completed.
- Initial project history created.
- Working documentation methodology established.

Status:

✅ Completed

---

# Milestone 2 — MVP Architecture and Security Boundary

## Goal

Translate the MVP definition into a minimum validated architecture before implementing infrastructure.

The objective is to determine what must actually exist for the remote local AI agent workflow to function safely and reproducibly.

## Deliverables

- MVP component map.
- Agent runtime evaluation or selection criteria.
- Messaging integration model.
- Communication-path definition.
- Authorized workspace model.
- File-system access boundary.
- Command execution model.
- Privileged-operation policy.
- Host access policy.
- Docker socket policy.
- Secret-handling requirements.
- Persistence requirements.
- Network requirements.
- Minimum service-boundary definition.
- Required architectural decision records.

## Exit Criteria

The project can answer:

1. Which agent runtime will be used for the first implementation.
2. How remote messages reach the local agent.
3. Which operations the agent can perform.
4. Where workspace operations are permitted.
5. How system-level operations are distinguished from normal operations.
6. How privileged operations are authorized.
7. Which services actually require containers.
8. Which services need to communicate.
9. Which persistent data requires storage.
10. Which secrets are required and how they are handled.
11. Whether any host ports must be exposed.

The minimum implementation architecture has been documented.

Status:

🟡 In Progress

---

# Milestone 3 — Docker Platform Implementation

## Goal

Design and implement the minimum reusable Docker platform required by the validated MVP architecture.

Docker is implemented as supporting infrastructure, not as an independent architecture exercise.

## Deliverables

- Required Docker services.
- Docker Compose architecture.
- Required networks.
- Required persistent volumes.
- Environment variable strategy.
- Secret integration approach.
- Required host mounts.
- Service configuration.
- Reproducible deployment procedure.
- Container validation.

## Exit Criteria

The required containers can be deployed successfully and support the defined MVP architecture without unnecessary networks, ports, volumes or privileged access.

Status:

⬜ Planned

---

# Milestone 4 — First AI Agent

## Goal

Deploy and validate the first AI agent runtime selected during Milestone 2.

Claw Code may be used if its actual capabilities satisfy the validated MVP requirements. The runtime must not be assumed before validation.

## Deliverables

- Agent runtime deployment.
- Required configuration.
- Authorized workspace integration.
- Defined execution capabilities.
- Authorization enforcement.
- Functional validation.

## Exit Criteria

The first local AI agent is operational within the defined workspace and execution boundaries.

Status:

⬜ Planned

---

# Milestone 5 — Remote Interaction

## Goal

Integrate the selected messaging platform and validate the complete remote-to-local workflow.

The initial preferred platform is Telegram.

## Deliverables

- Messaging integration.
- Remote instruction reception.
- User or request authorization model.
- Agent task dispatch.
- Authorized local execution.
- Result reporting.
- End-to-end validation.

## Exit Criteria

A remote user can send an authorized instruction through the selected messaging platform, the local agent can perform the permitted task, and the result is returned through the messaging channel.

Status:

⬜ Planned

---

# Milestone 6 — Local AI Platform and Future Services

## Goal

Expand the platform when additional services are justified by defined requirements.

Potential services may include:

- Ollama.
- Open WebUI.
- PostgreSQL.
- Redis.
- Monitoring.
- Logging.
- Secrets management.
- Backup strategy.

None of these services are mandatory unless required by a documented use case.

## Exit Criteria

Each additional service has:

- A documented purpose.
- Defined dependencies.
- Defined communication requirements.
- Defined persistence requirements.
- Defined security implications.
- Reproducible deployment.

Status:

⬜ Planned

---

# Future Milestone — Specialized AI Agents

## Goal

Design and deploy specialized agents using the platform established by the MVP.

Potential technologies may include:

- OpenAI Agents SDK.
- Google ADK.
- LangGraph.

Potential agent domains:

- Software development.
- Infrastructure.
- Cloud operations.
- Architecture analysis.
- FinOps.
- Security analysis.

Status:

⬜ Future

---

# Engineering Workflow

Every milestone follows the same sequence:

1. Plan.
2. Identify requirements.
3. Document.
4. Define security implications.
5. Design.
6. Implement.
7. Test.
8. Review.
9. Update documentation.
10. Commit.

No milestone is considered complete before documentation and validation are finished.

---

# Success Metrics

The project will be considered successful when:

- The MVP architecture follows defined requirements.
- Remote interaction with the local agent is functional.
- Local execution operates within explicit authorization boundaries.
- Infrastructure is reproducible.
- Architectural decisions are documented.
- Validation is evidence-based.
- Services are added only when justified by requirements.
- Future agents can be introduced without unnecessary architectural redesign.
