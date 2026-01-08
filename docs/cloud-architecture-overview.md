# Cloud/System Architecture Overview

This project is a monorepo with a React frontend and an Express API backed by an in-memory data store. The diagram below shows the high-level system context used during development.

```mermaid
flowchart LR
  user[User] -->|Browser| browser[Web Browser]
  browser --> frontend[React Frontend]
  frontend -->|REST calls /api| api[Express API]
  api -->|Queries| store[(In-memory Store<br/>SQLite via better-sqlite3)]

  classDef comp fill:#e3f2fd,stroke:#1976d2,stroke-width:1px,color:#0d47a1;
  classDef datastore fill:#fff3e0,stroke:#ff9800,stroke-width:1px,color:#e65100;
  class frontend,api comp;
  class store datastore;
```

- React app runs in the browser and invokes API endpoints under `/api/*`.
- Express API handles CRUD for tasks and reads/writes to an in-memory SQLite store.
- Local development defaults: API on port 3030; frontend dev server proxies `/api` to the backend.

## Sequence: Create TODO

```mermaid
sequenceDiagram
  participant User
  participant Browser
  participant Frontend
  participant API
  participant Store

  User->>Browser: Open app
  Browser->>Frontend: Render TaskForm
  User->>Frontend: Enter title, description, due date, priority
  Frontend->>API: POST /api/tasks JSON body
  API->>Store: Insert task
  Store-->>API: New task record
  API-->>Frontend: 201 Created + task
  Frontend->>Browser: Update TaskList
  Browser-->>User: New task appears
```
