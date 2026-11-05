# Action Log — Product Specification (curated case-study edition)

> **Source and status:** Adapted for recruitment from an existing evolving *Living Product Specification* (v0.26 draft) and corresponding verified implementation. This is a concise retrospective extract, **not** a claim that this exact document existed before development.

## 1. Problem and intent

A spreadsheet-based action register can become difficult to use when multiple people need reliable responsibility assignments, deadlines, traceable updates and coherent reporting. The aim was to validate a local, self-hosted web application that supports concurrent use while retaining important business rules.

## 2. Users and permissions

- **Reader:** read actions, history, summaries and reports.
- **Editor:** also create and edit actions.
- **Dictionary manager:** maintain specifically permitted business dictionaries, independently of action-edit rights.
- **Technical administrator:** administer accounts through Django's built-in administration.

Permissions must be enforced server-side, not only by hidden UI elements.

## 3. Core capabilities

### Action register
- Create, review, edit, filter and sort actions.
- Show descriptions, assignment, deadline and derived status.
- Preserve access to all register fields while prioritising the action, deadline and status visually.

### Safe concurrent editing
- Every write goes through one transactional application service.
- Changes carry a version check.
- A stale write returns a 409 conflict rather than silently overwriting another user's changes.
- The user can inspect the conflict without losing submitted text.
- Record create/update history with before/after snapshots.

### Reporting and Home
- Reuse existing status and summary calculations; avoid competing calculations in templates.
- Offer a compact overview and links to the register, reports, areas and meetings.
- Show an **Assigned actions** list sourced from existing `Accountable` data. Assignment does **not** imply real-time employee tracking.
- Keep the analytical dashboard and its charts alongside the simpler Home.

## 4. Representative acceptance criteria

| ID | Behaviour | Acceptance evidence sought |
|---|---|---|
| A-01 | Role access | Readers cannot modify actions; editors can where permitted. |
| A-02 | Concurrent updates | A stale version is rejected with HTTP 409 and submitted text is preserved. |
| A-03 | No-op save | Unchanged data does not create a misleading new revision. |
| A-04 | Home overview | Metrics use the established calculations and do not invent new statuses. |
| A-05 | Assigned actions | A person's assignment, description, deadline and status are accessible, including missing-data states. |
| A-06 | Navigation | Links honour access rights and keyboard focus remains manageable. |

## 5. Boundaries and open questions

- Full parity with the previous spreadsheet has not received a complete business sign-off.
- Some source-specific business interpretations remain open.
- Kanban, time tracking and business-impact/ROI tooling are **not** implemented modules of this local v0.1.
- This local release candidate is **not** a production or public-hosting release.
