# Engineering Notes

## Historical correctness

Payroll resolves the dated rate effective for each work entry instead of applying today's rate retrospectively. Financial history is preserved with reversals rather than destructive deletion.

## Money and reconciliation

Money uses fixed-precision storage and decimal calculations. A salary payment and its linked finance expense are coordinated so the same action is not recorded twice. Partial payments update the remaining balance instead of erasing the original obligation.

## Reliability and delivery

Database migrations run before application rollout. Health checks gate service startup, and backup/restore procedures target encrypted off-host storage with regular restore tests. Automated tests emphasize payroll boundaries, permissions, finance consistency, and security hardening.

