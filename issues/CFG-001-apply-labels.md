# CFG-001: Apply labels to finance-config-catalog

**Repo:** finance-config-catalog
**Owner type:** Technical Lead
**Labels:** `type:tech-debt`, `area:configuration`, `system:github`, `priority:critical`
**Milestone:** foundation-baseline

## Objective

Create the full label set so issues can be properly categorized.

## Scope

Run the label creation script against this repository. Same 40 labels as all finance repos.

## Dependencies

None.

## Acceptance Criteria

- [ ] All 40 labels created

## Definition of Done

`gh label list -R {owner}/finance-config-catalog` returns 40 labels.

## Execution

Same script as GOV-001, replace `REPO="{owner}/finance-config-catalog"`.
