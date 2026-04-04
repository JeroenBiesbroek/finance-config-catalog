# CFG-002: Enable branch protection on main

**Repo:** finance-config-catalog
**Owner type:** Technical Lead
**Labels:** `type:tech-debt`, `area:configuration`, `system:github`, `priority:critical`
**Milestone:** foundation-baseline

## Objective

Protect the main branch so all config changes require a reviewed PR.

## Scope

Same protection as other repos: required PR, 1 approval, stale review dismissal, no force push, no deletion.

## Dependencies

None.

## Acceptance Criteria

- [ ] Direct pushes to main blocked
- [ ] PRs require 1 approving review
- [ ] Stale reviews dismissed
- [ ] Force pushes disabled

## Definition of Done

`gh api repos/{owner}/finance-config-catalog/branches/main/protection` returns HTTP 200.

## Execution

```bash
gh api repos/{owner}/finance-config-catalog/branches/main/protection \
  -X PUT \
  -F "required_pull_request_reviews[required_approving_review_count]=1" \
  -F "required_pull_request_reviews[dismiss_stale_reviews]=true" \
  -F "enforce_admins=false" \
  -F "restrictions=null" \
  -F "required_status_checks=null" \
  -F "allow_force_pushes=false" \
  -F "allow_deletions=false"
```
