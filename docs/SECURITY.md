# Security

- Database-backed sessions use random tokens stored as SHA-256 hashes.
- Passwords use adaptive hashing; temporary-password and reset flows require controlled state changes.
- Server-side role and ownership checks protect every data boundary, including employee self-service.
- Origin/CSRF validation and SameSite cookies protect state-changing browser requests.
- Sensitive authentication paths are rate-limited at application and reverse-proxy layers.
- Zod schemas validate input; report and import routes constrain types and file signatures.
- Audit events and financial reversals preserve accountability.
- PostgreSQL remains on the internal deployment network; the public boundary is HTTPS.

This repository omits exact deployment endpoints, credentials, customer records, database dumps, and detailed assessment artifacts.

