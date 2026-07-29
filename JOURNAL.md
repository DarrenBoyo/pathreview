# JOURNAL

## Week 7 — Issue selection

**Issue link:** https://github.com/ascherj/pathreview/issues/117

**Issue title:** API docs don't include example curl commands

**Tier:** [x] Tier 1  [ ] Tier 2  [ ] Tier 3

**Problem summary:**
The API documentation explains each endpoint but does not include example curl commands that developers can use to test the API. This makes it harder for new contributors to verify their local setup and understand how each endpoint should be called. I will update the documentation by adding example curl commands for the documented endpoints so developers can test the API more easily.

**Branch name:** docs/117-api-curl-examples

**Setup confirmation:** [x] App runs locally at localhost:5173

**Cohort ledger:** [x] Issue added to cohort ledger

### Is this right for me?

- [x] The scope appears manageable within the course timeline.
- [x] I understand the area of the codebase involved.
- [x] The issue provides a good opportunity to learn more about the project.
- [x] I have a plan to reproduce the issue, implement a fix, and test my changes.

## Week 8 — Reproduction & solution planning

**Reproduction commit link:** [paste your GitHub commit link here]

**Reproduction summary:**
I reproduced Issue #117 by reviewing `docs/API.md` and confirming that the API endpoints are described without example `curl` commands. Developers currently have to inspect the backend routes or Swagger documentation to determine how to call and test the endpoints.

**PLAN.md link:** https://github.com/DarrenBoyo/pathreview/blob/docs/117-api-curl-examples/PLAN.md

**Walkthrough video (recommended):** Not recorded

**Blockers or open questions:**
I still need to confirm which endpoints require authentication and verify that every example works against the local API.