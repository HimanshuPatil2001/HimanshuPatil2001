# Contributing

## Documentation first

This project follows a documentation-first workflow. Before changing code,
confirm the relevant stage document exists under `docs/`.

| Stage | Folder |
|---|---|
| Request | `docs/01-request/` |
| Functional spec | `docs/02-fsd/` |
| Code plan | `docs/03-code-plan/` |
| Implementation log | `docs/04-implementation/` |
| Testing | `docs/05-testing/` |
| Deployment | `docs/06-deployment/` |
| Monitoring | `docs/07-monitoring/` |
| Handover | `docs/08-handover/` |

If a document is missing, the work has not started.

## Commit format

```
type(scope): summary (§stage)
```

- **type** — `docs`, `ci`, `chore`, `feat`, `fix`
- **scope** — the repo or area touched
- **§stage** — the documentation stage this advances

Example: `docs(meal-planner): add README with setup and usage (§00)`

## Rules

1. Never commit secrets. Use `.env.example` to document variable names.
2. Every behavioural change needs a changelog entry.
3. Architectural decisions get an ADR under `docs/04-implementation/decisions/`.

## Licence
MIT
