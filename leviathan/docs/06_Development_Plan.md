# 06 – Development Plan

*Everything here is a proposal pending team approval. Two schedules are kept apart: the **two-day documentation deadline** (Section 4) and the **longer software development schedule** (Section 5), whose real dates depend on the college's project deadline (pending confirmation).*

## 1. MVP Priorities

| Priority | Items |
|---|---|
| Must | FR-01–FR-05, FR-07–FR-09, FR-11–FR-16 |
| Should | FR-06, FR-10, FR-17 |
| Later (not MVP) | AI recommendations, team matching, personalised plans, notifications, third-party sign-in |

## 2. Phases and Deliverables

| Phase | Goal | Deliverables |
|---|---|---|
| 0 | Documentation | This documentation set, PDF/DOCX report |
| 1 | Foundation | Spring Boot project, MySQL schema, sample data, frontend skeleton |
| 2 | Core features | Opportunity and resource listing, search, filter, details, linking |
| 3 | User features | Registration/login, saved opportunities, deadline view, progress |
| 4 | Administration and security | Admin pages, role checks, validation, hardening |
| 5 | Quality and delivery | Test execution and report, bug fixes, final documentation, demo |

## 3. Work Breakdown Structure

1. **Project management:** task board, meetings, reviews.
2. **Database:** schema, constraints, sample data.
3. **Backend:** entities, repositories, services, controllers, security, validation, error handling.
4. **Frontend:** layout/CSS, listing and filters, details, login/register, saved page, admin forms.
5. **Quality:** test cases, test data, execution, defect tracking.
6. **Documentation:** keep docs aligned with reality; final report.

## 4. Two-Day Documentation Schedule (tentative)

| When | Tasks |
|---|---|
| Day 1 morning | Team reviews concept, scope and MVP; confirm institutional details and repository URL; approve or change proposals |
| Day 1 afternoon | Review Markdown documents and diagrams for accuracy; fix terminology |
| Day 2 morning | Review PDF/DOCX report; fill placeholders (college, department, course, year) |
| Day 2 afternoon | Upload to GitHub, verify links render, final read-through, submit |

## 5. Software Development Schedule (tentative, assumes about 8 weeks; adjust to the real deadline)

| Weeks | Phase | Milestone |
|---|---|---|
| 1 | 1 | M1: Project runs locally; schema created |
| 2–3 | 2 | M2: Browse/search/filter/details working with sample data |
| 4–5 | 3 | M3: Accounts, saving, progress working |
| 6 | 4 | M4: Admin interface and access control working |
| 7 | 5 | M5: Tests executed, defects triaged |
| 8 | 5 | M6: Fixes, final documentation, demonstration |

A milestone counts as reached only when its features are actually implemented and tested.

## 6. Collaboration and Git Workflow

- Branches: `main` (stable), `feature/*`, `fix/*`, `docs/*`.
- Pull requests need review by a team member other than the author.
- Small, frequent commits with descriptive messages; link PRs to issues.
- Issue board (To do / In progress / In review / Done); short weekly sync.
- With **no designated leader**, decisions are made by agreement; a rotating weekly facilitator keeps the agenda and follows up on open items.

## 7. Proposed Team Responsibilities (subject to team approval)

These are suggestions for discussion only; no work has been assigned or completed. Every member is expected to review others' pull requests.

| Member | Proposed primary area | Secondary |
|---|---|---|
| Dheeraj Mandal | Backend API and security | Code review |
| Jatin Lawaniya | Database schema and sample data | Backend services |
| Aakash Pal | Frontend student pages | UI consistency |
| Abhishek Tyagi | Admin pages and testing coordination | Documentation upkeep |

## 8. Risk Register

| ID | Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|---|
| R1 | Scope grows beyond MVP | High | High | Fixed MVP list; defer extras to "Later" |
| R2 | Team members unfamiliar with Spring Boot | Medium | High | Early spike, pair work, official guides |
| R3 | Outdated or wrong opportunity data | High | Medium | Admin verification, expiry marking, BR-06 notice |
| R4 | Integration problems between frontend and API | Medium | Medium | Agree API contract early; test with Postman |
| R5 | Merge conflicts, inconsistent code | Medium | Medium | Small PRs, branch rules, shared conventions |
| R6 | Security flaws (access control, XSS) | Medium | High | Planned tests TC-16, TC-19–TC-21, reviews |
| R7 | Too little time for testing | Medium | High | Write test cases early; reserve Week 7 |
| R8 | Unavailable team member | Medium | Medium | Shared ownership, documented work |
| R9 | Hosting unavailable | Medium | Low | Local demonstration as fallback |

Likelihood and impact ratings are team judgements, not measured values.

## 9. Dependencies and Decision Points

| Decision | Needed by |
|---|---|
| Approve MVP scope and requirement priorities | Documentation Day 1 |
| Confirm Java, Spring Boot, MySQL versions | Start of Phase 1 |
| Session vs token authentication | Phase 3 |
| Hosting approach | Phase 5 |
| Licence selection | Before public release |
| Whether to use a CSS framework | Phase 1 |

## 10. Definition of Done

A task is done when: the code is reviewed and merged through a pull request; it meets the relevant acceptance criteria; related tests have been written **and executed** with results recorded; no known Critical/High defects remain; input validation and role checks are in place; no secrets are committed; documentation is updated.

## 11. Future Enhancement Roadmap (after MVP, only if justified)

1. Notifications for approaching deadlines (e-mail service to be selected).
2. AI-based personalised recommendations.
3. Hackathon team matching.
4. Personalised preparation plans.
5. Further career-guidance features.
