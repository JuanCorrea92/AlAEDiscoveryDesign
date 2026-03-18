# Product Requirements Document (PRD) - TODO App Upgrade MVP

## 1. Overview

We are upgrading the existing TODO app from a minimal task tracker into a more practical planning tool while keeping the implementation simple enough for a teachable MVP. The current app only supports a task title and completion state. This upgrade adds due dates, priority levels, and task filters so users can better understand urgency and organize their work without adding backend complexity.

The final scope decision from the requirements follow-up is to keep the MVP lean: no backend changes, local-only storage, and a small set of high-value task management features. Visual overdue highlighting and advanced sorting were discussed in the meeting, but were explicitly deferred to Post-MVP in the Slack confirmation.

---

## 2. MVP Scope

- Add an optional `dueDate` field to each task.
- Store `dueDate` in ISO date format: `YYYY-MM-DD`.
- Add a `priority` field with allowed values `P1`, `P2`, and `P3`.
- Default `priority` to `P3` when not specified.
- Keep `title` as a required field.
- Ignore invalid `dueDate` values and treat them as absent.
- Add filter views for `All`, `Today`, and `Overdue`.
- In the `All` view, completed tasks remain visible.
- In the `Today` and `Overdue` views, only incomplete tasks are shown.
- Keep task storage local only.
- Do not introduce backend or external storage changes.

---

## 3. Post-MVP Scope

- Visually highlight overdue tasks so they stand out in the task list.
- Add task sorting with the following order:
- Overdue tasks first.
- Then by priority from `P1` to `P3`.
- Then by due date in ascending order.
- Tasks without a due date last.

---

## 4. Out of Scope

- Notifications.
- Recurring tasks.
- Multi-user support.
- Keyboard navigation enhancements.
- External storage integrations.