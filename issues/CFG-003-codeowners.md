# CFG-003: Create CODEOWNERS file

**Repo:** finance-config-catalog
**Owner type:** Technical Lead
**Labels:** `type:tech-debt`, `area:configuration`, `system:github`, `priority:critical`
**Milestone:** foundation-baseline

## Objective

Auto-assign Finance Lead as reviewer for all PRs in this repo.

## Dependencies

CFG-002 (branch protection must be enabled).

## Acceptance Criteria

- [ ] `CODEOWNERS` file exists at repo root
- [ ] PRs automatically request review from Finance Lead

## Definition of Done

Open a test PR. Verify Finance Lead is auto-requested. Close test PR.

## File Content

```
# Finance config — Finance Lead owns all config
* @{finance-lead-username}

# Control matrix changes require Finance Lead
/controls/ @{finance-lead-username}

# Mapping changes require Finance Lead
/mappings/ @{finance-lead-username}
```
