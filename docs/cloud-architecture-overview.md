# Cloud Architecture Overview

This monorepo contains a simple full-stack TODO application with a React frontend and an Express API. The frontend runs in the browser, sends HTTP requests to the backend, and the backend stores task data in an in-memory SQLite database.

## System Context

```mermaid
flowchart LR
    user[User]
    browser[Browser]
    frontend[React Frontend\npackages/frontend]
    api[Express API\npackages/backend]
    store[In-Memory SQLite Store]

    user --> browser
    browser --> frontend
    frontend -->|HTTP /api/tasks| api
    api -->|CRUD queries| store
```

## Create TODO Sequence

```mermaid
sequenceDiagram
    actor User
    participant Frontend as React Frontend
    participant API as Express API
    participant DB as In-Memory SQLite Store

    User->>Frontend: Enter task details and submit form
    Frontend->>API: POST /api/tasks
    API->>API: Validate title and request body
    API->>DB: INSERT new task record
    DB-->>API: Return created task id and data
    API-->>Frontend: 201 Created with task payload
    Frontend-->>User: Show new TODO in task list
```

## Notes

- The frontend and backend are developed in a single npm workspace monorepo.
- The API is implemented with Express and exposes task endpoints under `/api/tasks`.
- The current data store is in-memory, so task data does not persist across backend restarts.