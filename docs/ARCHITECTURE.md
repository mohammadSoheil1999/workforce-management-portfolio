# Architecture

The Next.js application owns both the rendered interface and server route boundary. Route handlers authenticate the session, apply role and ownership rules, validate input, and call focused payroll, finance, attendance, and reporting services. Prisma maps those services to PostgreSQL.

```mermaid
sequenceDiagram
  actor User
  participant Route as Server route
  participant Guard as Auth + authorization
  participant Service as Domain service
  participant DB as PostgreSQL transaction
  User->>Route: Submit work or payroll operation
  Route->>Guard: Validate session, role, origin, input
  Guard->>Service: Authorized command
  Service->>DB: Transactional read/write
  DB-->>Service: Committed result
  Service->>DB: Append audit event
  Service-->>Route: Safe DTO
  Route-->>User: Updated view
```

PostgreSQL is not exposed publicly in the documented deployment shape. Migrations run as a separate one-shot operation before the application is updated. Nginx provides the public reverse-proxy boundary.

