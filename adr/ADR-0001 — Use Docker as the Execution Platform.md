# ADR-0001 - Use Docker as the Execution Platform

## Status

Accepted

---

## Date

2026-07-18

---

## Context

The AI Local Lab is intended to host multiple AI-related services with different runtime requirements, including coding agents, local language models, databases and supporting infrastructure.

Installing every dependency directly on the host operating system would increase system complexity, make upgrades more difficult and reduce reproducibility.

A consistent execution platform is required to isolate services while keeping the laboratory portable and easy to rebuild.

---

## Decision

All application services in the AI Local Lab will run inside Docker containers.

Docker Compose will be used to orchestrate multi-container deployments.

The Ubuntu host operating system will remain as clean as possible and will only provide the infrastructure required to run Docker.

---

## Rationale

Docker provides process isolation, dependency isolation and reproducible environments.

Using containers allows every service to define its own runtime environment without interfering with the host or other services.

The same deployment can later be executed on another workstation, virtual machine or cloud provider with minimal changes.

This approach also aligns with modern infrastructure engineering and cloud-native practices.

---

## Alternatives Considered

### Install software directly on Ubuntu

Advantages

- Simpler initial setup.
- No container overhead.

Disadvantages

- Dependency conflicts.
- Difficult rollback.
- Harder maintenance.
- Lower portability.

Decision

Rejected.

---

### Python Virtual Environments

Advantages

- Excellent for Python projects.
- Lightweight.

Disadvantages

- Only isolates Python packages.
- Does not isolate operating system dependencies.
- Not suitable for Rust-based applications such as Claw Code.

Decision

Rejected.

---

### Virtual Machines

Advantages

- Complete operating system isolation.

Disadvantages

- Higher resource consumption.
- Slower provisioning.
- Less practical for small independent services.

Decision

Rejected.

---

## Consequences

### Positive

- Reproducible deployments.
- Better isolation.
- Easier upgrades.
- Simplified backup strategy.
- Infrastructure as Code.
- Portable architecture.

### Negative

- Additional learning curve.
- Slight increase in resource usage.
- Docker knowledge becomes a project prerequisite.

---

## Impact

This decision affects every service deployed within the AI Local Lab.

Future services such as Claw Code, Ollama, Open WebUI, PostgreSQL and custom AI agents will follow this deployment model.

---

## References

- Docker Documentation
- Docker Compose Documentation
- OCI Container Specification