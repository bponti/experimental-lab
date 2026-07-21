# Documentation Standards

## Purpose

This document defines the documentation standards used throughout the AI Local Lab project.

The objective is to ensure consistency, readability and maintainability across all project documentation.

---

# Documentation Principles

All documentation within this repository follows the principles below.

## 1. Single Source of Truth

Documentation must never duplicate information already managed by another system.

Examples:

- Git manages history.
- Git manages authorship.
- Git manages timestamps.
- Git manages versions through tags.

Documentation must only contain information that cannot be automatically retrieved.

---

## 2. Single Responsibility

Each document must answer one primary question.

| Document | Purpose |
|----------|---------|
| README | What is this project? |
| Project Overview | How is the project designed? |
| Roadmap | Where is the project going? |
| ADR | Why was this decision made? |
| Audit | What was verified? |
| Lab Journal | What happened during development? |

Documents should not overlap.

---

## 3. Documentation First

Architectural decisions should be documented before implementation whenever possible.

Documentation is considered part of the engineering process.

---

## 4. English Only

All project documentation is written in English.

This includes:

- Markdown documentation
- Comments
- Commit messages
- Branch names
- Docker services
- Folder names

Conversations during development may occur in another language.

---

## 5. Markdown Standard

Documentation is written using Markdown.

No proprietary documentation formats should be introduced unless justified by an Architecture Decision Record (ADR).

---

## 6. Evidence-Based Documentation

Technical statements should be supported by evidence whenever applicable.

Examples include:

- Terminal output
- Command results
- Log excerpts
- Screenshots
- Configuration files

Conclusions should be derived from collected evidence.

---

## 7. Living Documentation

Documentation evolves together with the project.

Documents must be updated whenever architectural or implementation changes occur.

---

## 8. Engineering Over Administration

Documentation exists to support engineering decisions.

Avoid maintaining metadata that is already tracked by Git.

Examples of information intentionally excluded:

- Author
- Last modified date
- Document version
- Revision history

---

# Documentation Categories

## Permanent Documentation

Defines stable aspects of the project.

Examples:

- README
- Project Overview
- ADRs
- Architecture

---

## Dynamic Documentation

Documents that evolve continuously.

Examples:

- Audit
- Lab Journal
- Roadmap

---

# Review Guidelines

Before creating a new document, verify:

- Does this document solve a specific problem?
- Does another document already contain this information?
- Is this information already tracked by Git?
- Can the document remain understandable six months from now?

If the answer suggests duplication, reconsider the document design
