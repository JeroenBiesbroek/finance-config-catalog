# CFG-006: Verify and complete account mapping with live data

**Repo:** finance-config-catalog
**Owner type:** Finance Lead
**Labels:** `type:change`, `area:sales-invoice`, `area:configuration`, `system:exact-online`, `process:requires-finance-approval`, `control:medium-impact`, `priority:critical`
**Milestone:** first-pilot

---

## Purpose

Verify that the existing account mapping table matches the actual Zoho Books product categories and Exact Online GL accounts in use. Add any missing mappings. This directly affects V-03 validation.

## Config Objects Affected

- `mappings/account/account-mapping-rules.md` — Mapping Table section

## Governance References

- Governed handoff: `finance-governance/ZOHOBOOKS_TO_EXACT_GOVERNED_HANDOFF.md` section 5 (line field 6: product_category → GL account via lookup)
- Validation rule: V-03 — GL account must exist in Exact chart of accounts
- PR template: finance-config-catalog specialized template

## Required Approvals

- Finance Lead (required — GL account mapping is a financial control)
- CFO: not required (unless GL structure is changed, which is out of scope)

## Scope

### In scope
- Export all product/service categories used on invoices in Zoho Books
- Export the relevant revenue GL accounts from Exact Online chart of accounts
- Cross-check the current 5-row mapping table against both sources
- Add missing category → GL account combinations
- Verify the "default" fallback account (8000) exists and is correct
- Confirm GL account descriptions match Exact Online

### Out of scope
- Adding new GL accounts to Exact Online (separate action)
- Changing Zoho Books product category structure
- Modifying the automation validation logic

## Execution Steps

1. In Zoho Books: list all product/service categories used on invoices in the last 12 months
2. In Exact Online: export revenue accounts (8000-8999 range or equivalent)
3. Compare to the current 5-row mapping table
4. Create feature branch: `feature/mapping-account-verify-live`
5. Edit `mappings/account/account-mapping-rules.md`:
   - Add missing category → GL account combinations
   - Verify existing entries match Exact Online
   - Confirm default account exists
6. Open PR using config-catalog PR template
7. Fill in:
   - **Affected configuration objects:** account mapping table
   - **Downstream coordination:** No automation code change needed — mapping format unchanged
   - **Validation performed:** Cross-checked against Zoho Books categories and Exact Online chart of accounts
8. Finance Lead reviews
9. Merge after approval
10. Close issue with PR link

## Validation Method

- Every product category used on Zoho Books invoices in the last 12 months has a mapping entry
- Every GL account in the table exists in the Exact Online chart of accounts
- GL account descriptions match Exact Online
- Default fallback account exists and is correct
- No duplicate category entries

## Rollback Method

Revert the PR commit. Previous mapping table is restored. No production impact.

## Evidence Required at Closure

- [ ] PR link with completed template
- [ ] Finance Lead approval on PR
- [ ] List of categories verified (documented in PR description)
- [ ] Any new mappings added (documented)
- [ ] Default account confirmed
- [ ] Merged to main

## Acceptance Criteria

- [ ] All active Zoho Books product categories have a mapping entry
- [ ] All GL accounts verified against Exact Online chart of accounts
- [ ] Default account confirmed
- [ ] Finance Lead approved
- [ ] PR merged to main
- [ ] Issue closed with PR link
