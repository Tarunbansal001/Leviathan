# 05 – Security and Test Plan

*Planning document. No implementation exists, so **every test case below is NOT RUN**.*

## 1. Security and Privacy Considerations

| Area | Planned control |
|---|---|
| Passwords | Salted adaptive hashing (e.g. BCrypt); no plain-text storage; no password in logs |
| Authentication | E-mail and password; generic login error messages; limit repeated failed attempts (recommended) |
| Authorisation | Role checks (STUDENT, ADMIN) on every protected endpoint server-side; admin accounts created by team only |
| Input validation | Server-side validation of type, length, format for all fields; parameterised queries (via JPA) to prevent SQL injection |
| Output encoding | Encode/escape data before inserting into HTML (e.g. use `textContent` instead of `innerHTML`) to prevent XSS |
| Link validation | Official/resource URLs must be well-formed with http/https only; reject `javascript:` and similar schemes; open external links with `rel="noopener noreferrer"` |
| Secrets | Database credentials and keys in environment variables or untracked config; `.gitignore` for config files; never commit secrets |
| Transport | HTTPS wherever the application is publicly deployed |
| Data protection | Collect minimum data (name, e-mail, password hash); restrict database access to the backend account; backup approach pending |
| CSRF/session | Choose session or token approach; if cookies are used, enable CSRF protection and secure cookie flags |
| Dependencies | Keep libraries updated; review known-vulnerability reports for dependencies |

## 2. Threat Assessment (proportionate to an MVP)

| Threat | Example | Mitigation |
|---|---|---|
| Injection | Malicious search text | Parameterised queries, validation |
| Cross-site scripting | Script in an opportunity description | Output encoding, admin-only content entry |
| Broken access control | Student calls admin endpoint | Server-side role checks, test TC-19 |
| Credential theft | Weak or leaked passwords | Hashing, minimum password rules, no secrets in repo |
| Malicious links | Phishing URL as "official link" | Admin review, scheme validation |
| Stale or wrong data | Wrong deadline | Admin verification step, BR-06 notice |

These follow the categories in the OWASP Top 10 (see references).

## 3. Test Strategy

| Level | Scope | Proposed tools |
|---|---|---|
| Unit | Service rules, validators | JUnit 5 |
| Integration | Controller + database | Spring Boot Test, test database |
| System | End-to-end flows in the browser | Manual scripts |
| Usability | Task completion by sample users | Observation checklist |
| Acceptance | Against SRS acceptance criteria | Team review |

**Risk-based priorities:** (1) access control and authentication, (2) correctness of deadlines and links, (3) search/filter, (4) data integrity, (5) usability and accessibility.

## 4. Test Cases

All statuses: **NOT RUN**.

| ID | Objective | Preconditions | Procedure | Expected result | Status |
|---|---|---|---|---|---|
| TC-01 | List published opportunities (FR-01) | Sample data with published and draft items | Open listing | Only published items shown | NOT RUN |
| TC-02 | Keyword search (FR-02) | Sample data | Search a known keyword | Matching items only; empty result handled | NOT RUN |
| TC-03 | Filter (FR-03) | Sample data with varied categories/deadlines | Apply category, skill, deadline filters | Results match all selected filters | NOT RUN |
| TC-04 | View details (FR-04) | Published opportunity exists | Open its detail page | Description, eligibility, deadline, official link shown correctly | NOT RUN |
| TC-05 | Linked resources (FR-05) | Opportunity linked to 2 resources | Open detail page | Exactly those 2 resources shown | NOT RUN |
| TC-06 | Resource list/search (FR-06) | Resources exist | Search/filter resources | Correct matches shown | NOT RUN |
| TC-07 | Register, login, logout (FR-07) | None | Register; log in; log out; try wrong password | Success flows work; wrong password rejected with generic message | NOT RUN |
| TC-08 | Save/unsave (FR-08) | Logged-in student | Save, save again, unsave | Saved once; duplicate prevented; unsave removes | NOT RUN |
| TC-09 | Saved list by deadline (FR-09) | Several saved items | Open Saved page | Sorted by deadline; passed deadlines marked | NOT RUN |
| TC-10 | Progress status (FR-10) | Logged-in student, resource exists | Set each status; reload | Status persists | NOT RUN |
| TC-11 | Admin creates opportunity (FR-11) | Admin logged in | Submit valid and invalid forms | Valid saved as draft; invalid rejected with messages | NOT RUN |
| TC-12 | Admin edit/archive/delete (FR-12) | Opportunity exists | Edit, archive, delete | Changes applied; archived hidden from students | NOT RUN |
| TC-13 | Admin manages resources/categories (FR-13, FR-17) | Admin logged in | Create, edit, delete | Changes persist; deleting an in-use category is handled safely | NOT RUN |
| TC-14 | Link/unlink resources (FR-14) | Opportunity and resource exist | Link then unlink | Detail page reflects each change | NOT RUN |
| TC-15 | URL validation (NFR-13, BR-04) | Admin form | Enter `javascript:alert(1)`, malformed URL, valid https URL | Unsafe/malformed rejected; valid accepted | NOT RUN |
| TC-16 | Password storage (NFR-03) | Test user registered | Inspect stored password value | Stored value is a salted hash, not the password | NOT RUN |
| TC-17 | Expiry marking (FR-16) | Opportunity with past deadline | View listing/detail | Marked as expired | NOT RUN |
| TC-18 | Publication status (FR-15) | Draft opportunity | View as student; publish; view again | Hidden while draft; visible after publishing | NOT RUN |
| TC-19 | Admin access control (NFR-04) | Student and visitor sessions | Call admin endpoints directly | 401/403 returned; no data changed | NOT RUN |
| TC-20 | Input validation / injection (NFR-05) | Search and forms | Submit SQL meta-characters, oversized input | No error leak, no data exposure, input rejected or safely handled | NOT RUN |
| TC-21 | Output encoding (NFR-06) | Test opportunity with `<script>` in text | View pages | Text displayed literally; no script runs | NOT RUN |
| TC-22 | Usability (NFR-01) | 3–5 sample students | Ask them to find and save an opportunity | Tasks completed; issues recorded | NOT RUN |
| TC-23 | Responsive/accessibility check (NFR-02, NFR-10) | Browser and keyboard | Resize; navigate by keyboard; run an accessibility checker | Layout adapts; core flows keyboard-usable; issues recorded | NOT RUN |
| TC-24 | Secret scan (NFR-12) | Repository | Search history and files for credentials | None found | NOT RUN |
| TC-25 | Provisional response time (NFR-07) | Sample dataset | Measure listing/search response time | Compare with provisional 2 s target; record result | NOT RUN |

## 5. Defect Reporting and Resolution Workflow

1. Tester opens a GitHub Issue with title, steps, expected vs actual result, environment, severity (Critical/High/Medium/Low).
2. Team triages and assigns an owner; label `bug`.
3. Fix on a `fix/…` branch; pull request references the issue.
4. Reviewer verifies; the related test case is re-run and its status updated with date and tester.
5. Issue closed only after retest. Critical/High defects block release of the milestone.
