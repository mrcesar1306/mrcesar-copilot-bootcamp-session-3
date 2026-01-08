# Product Requirements Document (PRD) - TODO App Upgrade (MVP + Post‑MVP)

## 1. Overview

We are upgrading the basic TODO app to support due dates, priorities, and filters so users can quickly identify urgent tasks and organize work without adding backend complexity. The MVP focuses on core fields and views with local-only storage; Post‑MVP adds visual highlighting and sorting behavior.

---

## 2. MVP Scope

- Due Date: Optional ISO `YYYY-MM-DD`; invalid values are ignored (treated as absent).
- Priority: Enum `"P1" | "P2" | "P3"` with default `"P3"`.
- Filters: Views for All, Today, Overdue.
- Storage: Local-only; no backend or external storage changes.
- Validation: `title` required; `priority` constrained to enum; `dueDate` optional.

---

## 3. Post-MVP Scope

- Overdue Highlighting: Visually emphasize overdue tasks (e.g., red styling).
- Sorting Rules: Overdue first → priority (P1→P3) → due date ascending → undated last.
- Priority Badges: Color-coded labels for priority (red P1, orange P2, gray P3).

---

## 4. Out of Scope

- Notifications.
- Recurring tasks.
- Multi-user support.
- Keyboard navigation / advanced accessibility features.
- External storage; remain local-only.
