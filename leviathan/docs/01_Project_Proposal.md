# 01 – Project Proposal

| | |
|---|---|
| **Project** | ORVO – *Discover. Prepare. Achieve.* |
| **Team** | RUDRAX: Dheeraj Mandal, Jatin Lawaniya, Aakash Pal, Abhishek Tyagi (no designated leader) |
| **College / Department / Course / Year** | *Pending confirmation* |
| **Status** | Proposal and design documentation. Development **not started**. |

## 1. Abstract

ORVO is a proposed web platform that unifies two activities students currently perform on separate websites: discovering career and skill-development opportunities, and preparing for them. The platform would list hackathons, internships, jobs and freelancing opportunities with eligibility details, deadlines and official links, and would connect each opportunity to relevant tutorials, practice questions, project guides and preparation material. Students could save opportunities and track deadlines and preparation progress; administrators would maintain content accuracy. The proposed implementation uses HTML, CSS and JavaScript for the frontend, Java with Spring Boot for the backend and MySQL for storage. This document defines the problem, objectives, scope, feasibility and a realistic MVP for a four-member student team.

## 2. Introduction and Background

Students are encouraged to participate in hackathons, apply for internships and build skills through projects. Information about such opportunities is spread across company career pages, specialised portals, social media and college notices. Preparation material (tutorials, practice problems, project ideas) is spread across a different set of sites. A student therefore repeats a cycle of finding an opportunity, working out what it requires and searching for ways to prepare, often under deadline pressure.

## 3. Problem Statement

Students discover opportunities on one platform but must search separately for tutorials, practice questions, project guidance, preparation material and deadline information. No single organised place connects an opportunity with the preparation needed for it.

## 4. Motivation and Need

- **Time:** repeated searching for related resources for every opportunity.
- **Missed deadlines:** deadlines are scattered and easy to overlook.
- **Unclear requirements:** eligibility and expected skills are not always easy to compare.
- **Lack of continuity:** discovery and preparation are treated as unrelated activities.

ORVO addresses these by making "what is the opportunity?" and "how do I get ready?" one connected journey.

## 5. Objectives

1. Provide a single place to browse, search and filter opportunities.
2. Show eligibility, deadlines and official application links for each opportunity.
3. Link opportunities to relevant preparation resources.
4. Allow students to save opportunities and track deadlines and progress.
5. Provide administrators with tools to keep information accurate.
6. Establish a maintainable architecture that can later support broader career-growth features.

## 6. Existing Approaches and Limitations

| Approach (examples) | Strength | Limitation relevant to ORVO |
|---|---|---|
| Opportunity portals and job boards (e.g. Devpost for hackathons, Internshala for internships, LinkedIn for jobs) | Large listings in a focused area | Usually concentrate on listing and applying; preparation material is outside their main purpose |
| Preparation platforms (e.g. LeetCode for coding practice, Coursera for courses) | Structured learning and practice | Not organised around specific opportunities and their deadlines |
| Social media, college notices, messaging groups | Fast sharing | Unstructured, hard to search, no deadline tracking |

These are general characterisations of the kinds of platforms available; sources are listed in [07 References and Glossary](07_References_and_Glossary.md). ORVO does not claim to replace them. Its proposed contribution is the *connection* between discovery and preparation, with official links preserved.

## 7. Proposed Solution

A web application with a student-facing interface and an administrator interface backed by a REST API and a relational database. Opportunities and resources are curated by administrators, classified by category, and linked to each other. Students search, filter, save and track. Applications are completed on the official external websites.

## 8. Target Users and Stakeholders

| Group | Interest |
|---|---|
| Students (primary users) | Discover and prepare for opportunities |
| Administrators | Maintain accurate listings and resources |
| Development team (RUDRAX) | Design, build, test and document ORVO |
| College evaluators | Assess the proposal and later the project |
| Opportunity providers (indirect) | Their official pages receive student traffic |

## 9. Scope and Exclusions

**In scope (proposed MVP):** browsing, search and filtering; opportunity details; resource access; registration/login; saved opportunities and deadline view; preparation-progress tracking; administrator content management.

**Out of scope for the MVP:** live scraping or automated aggregation from other sites; AI recommendations; team matching; personalised preparation plans; e-mail or push notifications; third-party sign-in; in-platform applications; mobile native apps; payments.

## 10. Proposed Modules

| Module | Responsibility |
|---|---|
| Opportunity Discovery | Listing, search, filter, details |
| Preparation Resources | Resource listing, resource-to-opportunity links |
| User Accounts | Registration, login, roles |
| Saved Items and Tracking | Saved opportunities, deadline view, progress |
| Administration | CRUD for opportunities, resources, categories; publication status |

## 11. Expected Outcomes

If the proposal is approved and implemented: a working MVP web application; a documented REST API; a normalised MySQL schema; a test suite and test report produced from real test execution; and updated documentation. *None of these exist yet.*

## 12. Feasibility

- **Technical:** HTML/CSS/JavaScript, Java/Spring Boot and MySQL are widely documented, free and suitable for a CRUD-centred application; the MVP avoids complex integrations.
- **Operational:** content is curated manually by administrators, avoiding dependence on external data feeds. Keeping content current requires ongoing effort.
- **Schedule:** feasibility depends on team availability; a phased plan with a fixed MVP is proposed in [06 Development Plan](06_Development_Plan.md).
- **Economic:** development uses free tools; hosting choice is pending.

## 13. Constraints and Assumptions

Assumptions (pending approval): at least one team member will act as administrator; opportunity data will be entered manually; the team is familiar enough with the chosen stack or will learn it; official links remain available. Constraints: two-day documentation deadline, student-team capacity, no prescribed college format.

## 14. Risks and Limitations

Stale or incorrect data; scope growth; uneven skill levels in the team; limited testing time; dependence on external sites whose URLs may change. Mitigations are in the [risk register](06_Development_Plan.md#8-risk-register).

## 15. Future Scope

AI-based personalised recommendations, hackathon team matching, personalised preparation plans and other career-guidance features, **only if justified** after the MVP is complete.

## 16. Conclusion

ORVO targets a specific, practical gap: the separation of opportunity discovery from preparation. A deliberately limited MVP on a familiar technology stack gives the team a realistic path from this proposal to a working system.

## 17. References

See [07 References and Glossary](07_References_and_Glossary.md).
