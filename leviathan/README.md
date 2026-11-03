# ORVO

**Discover. Prepare. Achieve.**

> **Status: Pre-development (documentation phase).** Only this documentation exists. No frontend, backend, database, API or test has been implemented. Everything below describes *proposed* functionality, pending team approval.

## Project Overview

ORVO is a proposed unified web platform that helps students discover career and skill-development opportunities (hackathons, internships, jobs, freelancing) and, from the same place, reach the resources needed to prepare for them (tutorials, practice questions, project guides and preparation material).

## Problem Statement

Students usually find opportunities on one set of websites and then search elsewhere for tutorials, practice material, project guidance and deadline information. This fragmentation costs time, causes missed deadlines and makes it harder to judge what an opportunity requires.

## Proposed Solution

ORVO connects *opportunity discovery* with *preparation*. A student finds an opportunity, reads its eligibility and deadline, opens linked preparation resources, saves the opportunity and tracks deadlines and progress. Administrators curate and maintain the listings and resources. ORVO links to official application pages; it does not process applications itself.

## Objectives

1. Provide one organised place to browse, search and filter opportunities.
2. Present eligibility, deadlines and official links clearly for each opportunity.
3. Link each opportunity to relevant preparation resources.
4. Let students save opportunities and track deadlines and preparation progress.
5. Give administrators a simple way to keep information accurate and current.
6. Build a maintainable foundation for future growth into a broader student career-growth platform.

## Initial Proposed Features (MVP candidates)

| Area | Proposed feature |
|---|---|
| Student | Browse, keyword search and filter opportunities; view details; open linked resources; register/log in; save opportunities; track deadlines and preparation progress |
| Administrator | Add, edit, archive/remove opportunities; manage resources and categories; link resources to opportunities; maintain deadlines, eligibility and source links; review published information |

Future enhancements (**outside the initial scope**): AI-based recommendations, hackathon team matching, personalised preparation plans, further career-guidance features.

## Target Users

- **Students** seeking opportunities and preparation help (primary users).
- **Administrators** (team-appointed content managers).

## Proposed Technology Stack

| Layer | Proposed technology |
|---|---|
| Frontend | HTML, CSS, JavaScript |
| Backend | Java with Spring Boot (REST API) |
| Database | MySQL |
| Collaboration | Git and GitHub |

Supporting tools (Spring Security, Maven, JUnit, etc.) are *recommendations*; see [Technology Stack](docs/04_Technology_Stack.md).

## Current Development Status

| Item | Status |
|---|---|
| Repository | Created (empty before this documentation) |
| Documentation | Draft, pending team approval |
| Frontend / Backend / Database / APIs | **Not started** |
| Tests | **Not run** (none implemented) |

## Team RUDRAX

Dheeraj Mandal, Jatin Lawaniya, Aakash Pal, Abhishek Tyagi. No designated team leader.

| Detail | Value |
|---|---|
| College | *Pending confirmation* |
| Department | *Pending confirmation* |
| Course | *Pending confirmation* |
| Academic year | *Pending confirmation* |
| Repository URL | *Pending confirmation* |

## Documentation Index

| Document | Description |
|---|---|
| [01 Project Proposal](docs/01_Project_Proposal.md) | Background, problem, objectives, scope, feasibility |
| [02 Software Requirements (SRS)](docs/02_Software_Requirements_SRS.md) | Functional and non-functional requirements, traceability |
| [03 System Design](docs/03_System_Design.md) | Architecture, workflows, API, data model |
| [04 Technology Stack](docs/04_Technology_Stack.md) | Technology choices and rationale |
| [05 Security and Test Plan](docs/05_Security_and_Test_Plan.md) | Security considerations and test cases (all NOT RUN) |
| [06 Development Plan](docs/06_Development_Plan.md) | Phases, schedule, workflow, risks |
| [07 References and Glossary](docs/07_References_and_Glossary.md) | Terms and sources |

Diagram sources (Mermaid, rendered automatically by GitHub): [architecture](docs/diagrams/architecture.mmd), [workflow](docs/diagrams/workflow.mmd), [use case](docs/diagrams/use_case.mmd), [database ER](docs/diagrams/database_er.mmd).

The academic report (`ORVO_Project_Proposal.pdf` and editable `.docx`) is stored in [`report/`](report/) if uploaded there.

## Planned MVP Scope

Opportunity listing, search and filter; opportunity details with linked resources; registration and login; saved opportunities with deadline view; simple preparation-progress tracking; an administrator interface for content management. Automated scraping, e-mail alerts, AI features and third-party sign-in are **excluded** from the MVP.

## Development Roadmap (proposed)

| Phase | Focus |
|---|---|
| 0 | Documentation (two-day deadline) |
| 1 | Setup, database schema, project skeleton |
| 2 | Core opportunity and resource features |
| 3 | Accounts, saving, progress tracking |
| 4 | Admin interface, security hardening |
| 5 | Testing, fixes, final documentation |

Details: [Development Plan](docs/06_Development_Plan.md).

## Contribution and Git Workflow

- `main` is protected: no direct pushes once development starts.
- Create short-lived branches such as `feature/<name>`, `fix/<name>` or `docs/<name>`.
- Open a pull request; at least one *other* team member reviews before merge.
- Use clear commit messages (e.g. `feat: add opportunity search endpoint`).
- Never commit passwords, API keys or database credentials.

## License

No license has been selected yet.
