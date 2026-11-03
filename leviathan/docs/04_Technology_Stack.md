# 04 – Technology Stack

*Nothing below has been installed or configured. "Confirmed" means stated in the team's project context; "Recommended" means proposed here for approval.*

## 1. Summary

| Layer | Technology | Status |
|---|---|---|
| Frontend | HTML, CSS, JavaScript | Confirmed (initial proposal) |
| Backend | Java, Spring Boot | Confirmed (initial proposal) |
| Database | MySQL | Confirmed (initial proposal) |
| Version control | Git, GitHub | Confirmed |
| Security library | Spring Security | Recommended |
| Build tool | Maven (or Gradle) | Recommended |
| Data access | Spring Data JPA | Recommended |
| Testing | JUnit 5, Spring Boot Test | Recommended |
| API testing | Postman or similar | Recommended (optional) |
| Hosting | Pending decision | Pending confirmation |

## 2. Frontend: HTML, CSS, JavaScript
- **Role:** structure (HTML), presentation and responsive layout (CSS), behaviour and API calls via `fetch` (JavaScript).
- **Why:** no build tooling, easy to learn and debug, supported by all browsers, sufficient for listing, forms and filters.
- **Alternatives:** React/Vue (better for complex UIs, steeper learning curve); Thymeleaf server-side templates (fewer moving parts, tighter coupling).
- **Trade-off:** more manual DOM handling; mitigate with small reusable JS modules and a consistent CSS structure. A CSS framework such as Bootstrap is an optional recommendation.

## 3. Backend: Java and Spring Boot
- **Role:** REST API, business rules, security enforcement, database access.
- **Why:** mature, well-documented, strong typing, common in industry and academic courses, built-in support for validation, security and testing.
- **Alternatives:** Node.js/Express (lighter), Django (batteries included). Not chosen because the team context specifies Java.
- **Trade-off:** more boilerplate and configuration than lighter frameworks.
- **Compatibility:** Spring Boot versions require specific minimum Java versions; the team must check the current Spring Boot documentation before project creation and pick a supported LTS Java release.

## 4. Database: MySQL
- **Role:** persistent relational storage.
- **Why:** free, widely used, fits structured data with many-to-many relations, good Spring/JPA support.
- **Alternatives:** PostgreSQL (richer features), H2 (in-memory, useful only for tests).
- **Considerations:** use InnoDB for foreign keys and transactions; utf8mb4 character set; an `.sql` schema file or migration tool (Flyway/Liquibase, optional) under version control.

## 5. API Design Approach
REST over HTTPS, JSON payloads, resource-oriented paths, standard HTTP status codes, pagination for lists, consistent error format, input validation with Bean Validation. See [03 System Design](03_System_Design.md#6-proposed-api-responsibilities-examples).

## 6. Development Environment and Tools (proposed)
JDK (LTS), IDE (IntelliJ IDEA, Eclipse or VS Code), MySQL server and a client (MySQL Workbench or CLI), modern browser with developer tools, Git client. Each member should use the same JDK/MySQL major versions to avoid "works on my machine" problems.

## 7. Version-Control Workflow
Git with GitHub: protected `main`, feature branches, pull requests with peer review, issues for task tracking (optional GitHub Projects board). See [06 Development Plan](06_Development_Plan.md#6-collaboration-and-git-workflow).

## 8. Deployment Options (not decided)

| Option | Pros | Cons |
|---|---|---|
| Run locally for demonstration | Free, no setup risk | Not publicly accessible |
| Student/free-tier cloud hosting | Public URL | Limits, possible changes in free plans; must be checked at the time |
| College server (if available) | Possibly free | Depends on college permission |

Recommendation: plan for local demonstration first; treat public hosting as optional.

## 9. Dependencies and Compatibility
Java ↔ Spring Boot version; Spring Boot ↔ MySQL driver and Hibernate version; browser support for JavaScript features used. Pin dependency versions in the build file and review them before adding anything new.

## 10. Advantages and Limitations (overall)
**Advantages:** familiar technologies, free, well documented, suitable for an MVP. **Limitations:** no framework on the frontend, manual content entry, no search engine beyond SQL queries in the MVP.
