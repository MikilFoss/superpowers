# Spot-Check Subagent Prompt Template

Use this template when dispatching a spot-check subagent to verify acceptance criteria.

**Purpose:** End-to-end verification that the feature actually works, beyond unit tests.

```
Task tool (spot-check):
  description: "Spot-check: [feature name] acceptance criteria"
  prompt: |
    Verify these acceptance criteria for the implementation:

    ## Acceptance Criteria

    [PASTE acceptance criteria from plan header — the checkbox list]

    ## App Details

    - **URL**: [app URL — e.g., http://localhost:5173 for frontend, http://localhost:3001/api for backend]
    - **Auth**: [any auth setup needed — tokens, cookies, login flow, or "none"]
    - **Setup**: [any required state — seed data, running services, env vars]

    ## Your Job

    For each acceptance criterion, determine the check type and verify:

    **UI criteria** (things visible/interactive in browser):
    - Write a Playwright script to navigate, interact, and verify
    - Take screenshots as evidence of pass/fail

    **API criteria** (endpoint behavior):
    - Write a script using fetch/curl to hit the endpoint
    - Verify status codes, response bodies, headers

    **Integration criteria** (cross-system behavior):
    - Combine browser + API checks as needed
    - Verify end-to-end flow produces expected state

    ## Report Format

    For each criterion from the list:
    - ✅ PASS: [what was verified, with evidence — screenshot path or response body]
    - ❌ FAIL: [expected vs actual, with screenshot/output]

    **Summary:** X/Y criteria passing.

    If any FAIL, describe exactly what's wrong and where so an implementer can fix it.
    Include file paths and specific behavior observed vs expected.
```
