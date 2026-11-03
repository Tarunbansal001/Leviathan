# 02 – Software Requirements Specification (SRS)

*Draft v0.1, proposed requirements pending team approval. Structure follows the general approach of ISO/IEC/IEEE 29148:2018 but is simplified for a student project.*

## 1. Purpose and Scope

This SRS defines the proposed requirements of **ORVO**, a web platform connecting students with career and skill-development opportunities and related preparation resources. It covers the MVP only. No part of the system has been implemented.

## 2. Product Perspective

ORVO is a new, standalone web application. It does not integrate with external opportunity sites; it stores curated information and links to official pages. Context: browser → frontend → REST API → MySQL (see [03 System Design](03_System_Design.md)).

## 3. User Classes and Roles

| Role | Description | Access |
|---|---|---|
| Visitor | Unauthenticated user | Browse, search, filter, view opportunities and resources (proposed) |
| Student | Registered user | Visitor access plus save opportunities, track progress |
| Administrator | Team-appointed content manager | Manage opportunities, resources, categories |

## 4. Operating Environment

Modern desktop and mobile web browsers (current Chrome, Firefox, Edge, Safari); server running Java (version *pending confirmation*, recommended current LTS) and MySQL (version pending confirmation). Deployment target pending.

## 5. Definitions

See [07 References and Glossary](07_References_and_Glossary.md).

## 6. Functional Requirements

Priority: **M** = Must (MVP), **S** = Should (MVP if time permits).

| ID | Requirement | Pri |
|---|---|---|
| FR-01 | The system shall list published opportunities. | M |
| FR-02 | The system shall allow keyword search over opportunity title, description and required skills. | M |
| FR-03 | The system shall allow filtering by category/type, required skills, eligibility text, and deadline, where the data exists for the listing. | M |
| FR-04 | The system shall show opportunity details: description, category, eligibility, skills, deadline, official application link. | M |
| FR-05 | The system shall show the preparation resources linked to an opportunity. | M |
| FR-06 | The system shall list and search preparation resources (tutorials, practice questions, project guides, learning material) independently of opportunities. | S |
| FR-07 | The system shall let a visitor register and log in, and let a user log out. | M |
| FR-08 | A logged-in student shall be able to save and unsave an opportunity. | M |
| FR-09 | A student shall be able to view saved opportunities sorted by deadline, with passed deadlines clearly marked. | M |
| FR-10 | A student shall be able to set a preparation status (not started, in progress, completed) for a resource. | S |
| FR-11 | An administrator shall be able to create an opportunity with required fields. | M |
| FR-12 | An administrator shall be able to edit, archive or delete an opportunity. | M |
| FR-13 | An administrator shall be able to create, edit and delete resources. | M |
| FR-14 | An administrator shall be able to link and unlink resources to/from opportunities. | M |
| FR-15 | Each opportunity shall have a status (draft, published, archived); only published items are visible to students. | M |
| FR-16 | The system shall mark opportunities whose deadline has passed as expired. | M |
| FR-17 | An administrator shall be able to manage categories. | S |

## 7. Non-Functional Requirements

Numeric targets are **provisional** and have no measured basis yet.

| ID | Category | Requirement |
|---|---|---|
| NFR-01 | Usability | A first-time student should be able to find an opportunity and open its details without instructions (to be checked in usability testing). |
| NFR-02 | Responsiveness | Pages shall adapt to common mobile and desktop screen widths. |
| NFR-03 | Security | Passwords shall be stored only as salted hashes using a recommended adaptive algorithm (e.g. BCrypt); never in plain text. |
| NFR-04 | Security | Server-side role checks shall protect all administrator endpoints. |
| NFR-05 | Security | All user-supplied input shall be validated on the server. |
| NFR-06 | Security | Output rendered in the browser shall be encoded or sanitised to prevent script injection. |
| NFR-07 | Performance (provisional) | Listing and search pages should respond in about 2 seconds under typical demonstration load; to be reviewed after measurement. |
| NFR-08 | Reliability | Database constraints (keys, uniqueness, not-null) shall protect data integrity. |
| NFR-09 | Maintainability | Code shall follow a layered structure (controller, service, repository) with consistent naming. |
| NFR-10 | Accessibility (goal) | Semantic HTML, keyboard operability, text alternatives and adequate contrast, aiming toward WCAG 2.2 AA where feasible. |
| NFR-11 | Privacy | Only the minimum personal data (name, e-mail, password hash) shall be collected. |
| NFR-12 | Security | Secrets and credentials shall be kept outside the repository (environment variables or untracked configuration). |
| NFR-13 | Data quality | Official URLs shall be accepted only with http or https schemes and be well-formed. |

## 8. External Interface Requirements

- **User interface:** HTML pages for listing, filters, details, saved items, login/registration, admin forms.
- **Software interface:** JSON REST API between frontend and backend; SQL access from backend to MySQL.
- **External links:** official opportunity and resource URLs opened in the browser; no programmatic integration in the MVP.

## 9. Data Requirements

Entities: User, Category, Opportunity, Resource, OpportunityResource (link), SavedOpportunity, PreparationProgress. Key fields: titles, descriptions, eligibility, required skills, deadline, official URL, resource URL, status, timestamps. See [database ER diagram](diagrams/database_er.mmd) and [03 System Design](03_System_Design.md#7-proposed-database-design).

## 10. Authentication and Access Control

Registration and login with e-mail and password; role stored per user (STUDENT or ADMIN); stateless token or server session (*decision pending*); administrator accounts are created by the team, not by public registration.

## 11. Business Rules

| ID | Rule |
|---|---|
| BR-01 | Only PUBLISHED opportunities are visible to visitors and students. |
| BR-02 | Each opportunity belongs to exactly one category. |
| BR-03 | A student can save a given opportunity only once. |
| BR-04 | Each opportunity must carry an official source URL. |
| BR-05 | Only administrators may create, change or delete content. |
| BR-06 | ORVO is a reference tool; students must confirm details on the official site before applying. |
| BR-07 | Content is entered manually; ORVO does not scrape other websites. |

## 12. Constraints, Dependencies and Assumptions

Constraints: student-team capacity, fixed technology stack, deadlines. Dependencies: availability of the chosen tools, correctness of manually entered data. Assumptions: administrators will keep data current; the team approves this scope.

## 13. Acceptance Criteria (summary)

| Requirement | Accepted when (proposed) |
|---|---|
| FR-01–FR-04 | Seeded opportunities can be listed, searched, filtered and opened; details match stored data. |
| FR-05, FR-06 | Linked resources appear on the detail page; unlinked resources do not. |
| FR-07 | A new user can register, log in and log out; invalid credentials are rejected. |
| FR-08–FR-10 | Saved items persist across sessions; duplicate saves are prevented; progress status persists. |
| FR-11–FR-17 | An administrator can perform each change and the result is visible to students only when published. |
| NFR-03–NFR-06, NFR-12 | Verified by security checks listed in [05 Security and Test Plan](05_Security_and_Test_Plan.md). |

## 14. Requirement Traceability

| Objective (01 Proposal §5) | Requirements | Planned tests |
|---|---|---|
| 1 Browse/search/filter | FR-01, FR-02, FR-03, FR-16 | TC-01, TC-02, TC-03, TC-17 |
| 2 Details and official links | FR-04, BR-04, NFR-13 | TC-04, TC-15 |
| 3 Link to resources | FR-05, FR-06, FR-14 | TC-05, TC-06, TC-14 |
| 4 Save and track | FR-07–FR-10 | TC-07, TC-08, TC-09, TC-10 |
| 5 Admin maintenance | FR-11–FR-15, FR-17 | TC-11, TC-12, TC-13, TC-18 |
| 6 Maintainable foundation | NFR-09 | Code review checklist |
| Security and quality | NFR-01, NFR-02, NFR-03–NFR-08, NFR-10, NFR-12 | TC-16, TC-19–TC-25 |

All tests are currently **NOT RUN**.
