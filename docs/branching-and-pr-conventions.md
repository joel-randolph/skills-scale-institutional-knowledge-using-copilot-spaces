# Branching and PR Conventions

## Branch Naming

Use a short, descriptive name with a slash-separated prefix:

| Prefix | Use when |
|--------|----------|
| `feature/` | New functionality |
| `fix/` | Bug fixes in non-production code |
| `hotfix/` | Urgent fix to production |
| `chore/` | Maintenance, dependency updates, tooling |
| `docs/` | Documentation-only changes |

**Format:** `<prefix>/<short-description>` or `<prefix>/<short-description>/issue-<number>`

**Examples:**
```
feature/user-auth
fix/login-redirect
hotfix/null-pointer-crash
chore/upgrade-node-18
docs/process-improvements/issue-4
```

## Commit Messages

Follow the [Conventional Commits](https://www.conventionalcommits.org/) style:

```
<type>(<scope>): <short summary>

[optional body]

[optional footer: Closes #<issue-number>]
```

**Types:** `feat`, `fix`, `docs`, `chore`, `refactor`, `test`, `ci`

**Examples:**
```
feat(auth): add OAuth2 login flow
fix(api): handle null response from user service
docs(readme): update setup instructions
```

- Keep the subject line under 72 characters.
- Use the imperative mood: "add feature" not "added feature".
- Reference issues in the footer: `Closes #42`.

## PR Size Guidance

- Aim for **≤ 400 lines changed** per PR.
- Large features should be broken into smaller, independently-reviewable PRs (e.g., data model, API, UI).
- Avoid mixing refactors and feature work in the same PR unless tightly coupled.

## Required CI Checks

Before requesting review, all of the following must pass:

- [ ] Automated tests (unit + integration)
- [ ] Linting / code style
- [ ] Security scan
- [ ] Build succeeds

## Review Policy

- Require **at least one approval** from a team member before merging.
- Author should not merge their own PR unless explicitly agreed by the team.
- Reviewers should complete review within **1 business day**.
- Unresolved review threads must be addressed or explicitly marked "won't fix" with a reason before merge.

## Linking Issues

- Include `Closes #<issue-number>` or `Fixes #<issue-number>` in the PR description to auto-close the linked issue on merge.
- If the PR partially addresses an issue, use `Part of #<issue-number>` instead.

## PR Description Template

Copy the following template into every new PR description:

```markdown
## Summary
<!-- What does this PR do? Why? -->

## Issue Link
Closes #<issue-number>

## Acceptance Criteria
<!-- List the criteria from the issue or define them here -->
- [ ] ...

## Testing Steps
<!-- How can a reviewer manually verify this change? -->
1. ...
2. ...

## Notes / Migration Steps
<!-- Any special deployment steps, migration scripts, or things reviewers should know? -->
N/A
```

## PR Title Conventions

PR titles should follow the same Conventional Commits format as commit messages:

```
<type>(<scope>): <short summary>
```

This keeps the squash-merge commit history consistent with PR history.

## Short Example

**Branch:** `feature/payment-retry/issue-88`

**PR title:** `feat(payments): add automatic retry on transient errors`

**PR body:**
```markdown
## Summary
Adds up to 3 automatic retries with exponential backoff when the payment
gateway returns a 5xx response. Prevents unnecessary user-facing errors
during brief outages.

## Issue Link
Closes #88

## Acceptance Criteria
- [ ] Retries fire up to 3 times with 1s/2s/4s delays
- [ ] Non-retryable errors (4xx) are not retried
- [ ] Unit tests cover retry logic

## Testing Steps
1. Run `npm test` — all tests pass.
2. Simulate a 503 from the gateway mock; verify 3 retry attempts in logs.

## Notes / Migration Steps
N/A
```
