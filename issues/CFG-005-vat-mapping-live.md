# CFG-005: Verify and complete VAT mapping with live data

**Repo:** finance-config-catalog
**Owner type:** Finance Lead
**Labels:** `type:change`, `area:vat-tax`, `area:configuration`, `system:exact-online`, `system:zoho-books`, `process:requires-finance-approval`, `process:requires-cfo-approval`, `control:high-impact`, `priority:critical`
**Milestone:** first-pilot

---

## Purpose

Verify that the existing VAT mapping table matches the actual Zoho Books tax rates and Exact Online VAT codes in use. Add any missing mappings. This directly affects V-02 validation and has high control impact.

## Config Objects Affected

- `mappings/vat/vat-mapping-rules.md` — Mapping Table section

## Governance References

- Governed handoff: `finance-governance/ZOHOBOOKS_TO_EXACT_GOVERNED_HANDOFF.md` section 5 (line field 3: tax_percentage → VAT code via lookup)
- Validation rule: V-02 — VAT code must match Exact allowed values
- Control: CTRL-SI-005 — VAT code validation
- Change process: requires Finance Lead + CFO approval (VAT-sensitive)

## Required Approvals

- Finance Lead (required)
- CFO (required — VAT/tax-related change)

## Scope

### In scope
- Export all tax rates used on invoices in Zoho Books
- Export all VAT codes configured in Exact Online
- Cross-check current mapping table against both sources
- Add any missing mappings
- Correct any incorrect mappings
- Confirm that the 5 existing entries (21%, 9%, 0%, reverse charge EU, export) are correct for this administration

### Out of scope
- Changing Zoho Books tax rate configuration
- Changing Exact Online VAT code configuration
- Modifying the automation validation logic

## Execution Steps

1. In Zoho Books: list all tax rates used on invoices in the last 12 months
2. In Exact Online: list all active VAT codes
3. Compare to the current 5-row mapping table
4. Create feature branch: `feature/mapping-vat-verify-live`
5. Edit `mappings/vat/vat-mapping-rules.md`:
   - Correct any mismatches
   - Add missing rate → code combinations
   - Verify the descriptions match Exact Online labels
6. Open PR using config-catalog PR template
7. Fill in:
   - **Affected configuration objects:** VAT mapping table
   - **Downstream coordination:** No automation code change needed — mapping format unchanged
   - **Validation performed:** Cross-checked against Zoho Books tax rates and Exact Online VAT codes
8. Finance Lead reviews
9. CFO reviews (VAT-sensitive)
10. Merge after both approvals
11. Close issue with PR link

## Validation Method

- Every tax rate used on Zoho Books invoices in the last 12 months has a mapping entry
- Every VAT code in the table exists and is active in Exact Online
- Descriptions match Exact Online VAT code descriptions
- No duplicate tax_percentage entries (except where the same rate maps differently based on transaction type, which must be documented)

## Rollback Method

Revert the PR commit. Previous mapping table is restored. No production impact — sync automation is not yet live.

## Evidence Required at Closure

- [ ] PR link with completed template
- [ ] Finance Lead approval on PR
- [ ] CFO approval on PR
- [ ] List of tax rates verified (documented in PR description)
- [ ] Any new mappings added (documented)
- [ ] Any corrections made (documented with reason)
- [ ] Merged to main

## Acceptance Criteria

- [ ] All Zoho Books tax rates in use have a valid mapping
- [ ] All VAT codes verified against Exact Online
- [ ] Finance Lead approved
- [ ] CFO approved
- [ ] PR merged to main
- [ ] Issue closed with PR link
