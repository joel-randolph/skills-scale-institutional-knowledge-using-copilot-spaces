# Release Checklist

Use this checklist for every planned release. The **Release Manager** (usually the PM or a designated lead) is responsible for ensuring all items are complete.

---

## Pre-Release Gating

- [ ] All acceptance criteria for release scope are verified and signed off by QA.
- [ ] No open P0/P1 bugs targeting this release.
- [ ] All PRs in scope are merged to the release branch.
- [ ] CI pipeline is green on the release branch (tests, lint, security scan, build).
- [ ] Release notes drafted and reviewed (see template below).
- [ ] Stakeholders and support team notified of upcoming release window.
- [ ] Runbook / deployment plan reviewed by Release Manager and on-call engineer.
- [ ] Rollback plan confirmed (see Rollback Steps below).
- [ ] Database migrations (if any) tested in staging and rollback scripts verified.
- [ ] Feature flags reviewed — confirm which flags to enable/disable at release.
- [ ] Monitoring dashboards and alerts confirmed active for release window.

**Responsible roles:** Release Manager, QA Lead, On-call Engineer

---

## Deployment Steps

1. Announce deployment start in team channel (include expected duration and rollback threshold).
2. Merge release branch to `main` (or trigger deployment pipeline for your environment).
3. Deploy to production (or promote from staging per your pipeline).
4. Monitor error rate, latency, and key business metrics for **15 minutes** post-deploy.
5. Run smoke tests against production (see post-deploy verification below).
6. Announce deployment complete or initiate rollback if verification fails.

**Responsible roles:** On-call Engineer, Release Manager

---

## Rollback Steps

If a critical issue is detected post-deploy:

1. **Decision:** Release Manager or on-call engineer declares rollback (within agreed SLO window).
2. **Revert deploy:** Re-deploy the previous production artifact/image, or revert the merge commit and redeploy.
3. **Database:** If a migration was applied, execute the rollback migration script (must be prepared pre-release).
4. **Feature flags:** Disable any newly enabled flags.
5. **Verify:** Confirm error rate and latency return to baseline.
6. **Communicate:** Notify stakeholders of rollback and ETA for re-release.
7. **Post-mortem:** Open a follow-up issue to track root cause and re-release plan.

**Responsible roles:** On-call Engineer, Release Manager, PM

---

## Post-Deploy Verification

- [ ] Smoke tests pass in production.
- [ ] Key user flows tested manually (login, core feature, checkout, etc.).
- [ ] No spike in error rate or latency on dashboards.
- [ ] No new alert fires within 15 minutes of deploy.
- [ ] Release notes or changelog published (in-app, docs site, or announcement channel).
- [ ] Support team briefed on any user-visible changes.

**Responsible roles:** QA, On-call Engineer, Release Manager

---

## Release Notes Template

```markdown
## Release vX.Y.Z — YYYY-MM-DD

### What's New
- Feature A: brief description of user-facing value.
- Feature B: brief description.

### Bug Fixes
- Fixed: description of what was broken and what was fixed.

### Breaking Changes / Migration Steps
- None. OR: Describe what changes and what users/operators need to do.

### Known Issues
- None. OR: Describe any known limitations in this release.

### Rollback Instructions
- See [release runbook](./release-checklist.md#rollback-steps).
```
