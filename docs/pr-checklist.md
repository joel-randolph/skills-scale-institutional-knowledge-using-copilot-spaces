# PR Checklist

Copy this checklist into your PR description before requesting review. Both the author and reviewers should verify each item.

## Author Checklist

- [ ] **Tests** — New/changed code has corresponding unit or integration tests; all existing tests pass.
- [ ] **Lint** — Code passes the project linter (`npm run lint` / `make lint` / equivalent).
- [ ] **Security scan** — CI security scan passes with no new high/critical findings.
- [ ] **Changelog / Release notes** — `CHANGELOG.md` updated (or a release note added) if this change is user-visible.
- [ ] **Documentation updated** — Relevant docs (README, API docs, runbooks) reflect any behavioral changes.
- [ ] **Migration steps** — If DB schema, config, or environment changes are required, migration steps are documented in the PR description.
- [ ] **PR size** — PR is ≤ 400 lines changed, or a justification for a larger PR is provided.
- [ ] **Issue linked** — PR description contains `Closes #<issue>` or `Part of #<issue>`.

## Reviewer Checklist

- [ ] **Correctness** — Code does what the PR description and issue say it should.
- [ ] **Tests sufficient** — Test coverage addresses the main scenarios and edge cases.
- [ ] **No obvious security issues** — No hardcoded secrets, unvalidated inputs, or broken access control.
- [ ] **Naming and readability** — Variables, functions, and files are clearly named and follow existing conventions.
- [ ] **Docs and comments** — Complex logic is explained; public interfaces are documented.
- [ ] **Migration safe** — Deployment/migration steps are complete and reversible if needed.
