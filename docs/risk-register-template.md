# Risk Register Template

Use this table to track project risks. Update at least weekly (or after any significant event). The Risk Owner is responsible for monitoring status and executing the mitigation.

## Risk Register

| ID | Description | Impact | Likelihood | Owner | Mitigation | Status | Last Updated |
|----|-------------|--------|------------|-------|------------|--------|--------------|
| R-001 | Third-party API unavailable during launch | High | Medium | DevOps Engineer | Implement retry logic and circuit breaker; test with mock outage in staging | Open | YYYY-MM-DD |
| R-002 | _(add your risk here)_ | _(High/Medium/Low)_ | _(High/Medium/Low)_ | _(name/role)_ | _(mitigation plan)_ | _(Open/Mitigated/Closed)_ | YYYY-MM-DD |

---

## Field Definitions

| Field | Description |
|-------|-------------|
| **ID** | Unique identifier (e.g., R-001). Increment sequentially. |
| **Description** | One-sentence description of the risk event. |
| **Impact** | Business/project impact if the risk materializes: `High`, `Medium`, or `Low`. |
| **Likelihood** | Probability of occurrence: `High`, `Medium`, or `Low`. |
| **Owner** | Person or role responsible for monitoring and mitigating this risk. |
| **Mitigation** | Concrete actions to reduce likelihood or impact. |
| **Status** | `Open` (active risk), `Mitigated` (mitigation applied), or `Closed` (risk no longer relevant). |
| **Last Updated** | ISO date (YYYY-MM-DD) of the last status update. |

---

## Usage Notes

- Add new risks as they are identified in standups, retrospectives, or risk reviews.
- Review the register in the weekly delivery sync and update Status and Last Updated.
- Close risks that are no longer relevant; do not delete rows (preserves history).
- Escalate any risk rated **High Impact + High Likelihood** to the PM and sponsor immediately.
