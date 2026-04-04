# CFG-004: Populate debtor mapping with live data

**Repo:** finance-config-catalog
**Owner type:** Finance Lead
**Labels:** `type:change`, `area:sales-invoice`, `area:configuration`, `system:exact-online`, `system:zoho-books`, `process:requires-finance-approval`, `control:medium-impact`, `priority:critical`
**Milestone:** first-pilot

---

## Purpose

Replace the example debtor mapping entry with actual Zoho Books customer → Exact Online debtor code data. This is the first pilot of the governed config change flow and a prerequisite for any sales invoice sync.

## Config Objects Affected

- `mappings/debtor/debtor-mapping-rules.md` — Mapping Table section

## Governance References

- Governed handoff: `finance-governance/ZOHOBOOKS_TO_EXACT_GOVERNED_HANDOFF.md` section 5 (field mapping, header row 1: customer_id → Debtor code via lookup)
- Validation rule: V-01 — Debtor must exist in Exact Online
- Control: CTRL-SI-003 — Debtor consistency
- PR template: finance-config-catalog specialized template (downstream coordination section)

## Required Approvals

- Finance Lead (required — owns mapping data)
- CFO: not required (no VAT/tax impact)

## Scope

### In scope
- Export active customer list from Zoho Books (customer_id + customer name)
- Export debtor list from Exact Online (debtor code + debtor name)
- Match each active Zoho Books customer to an Exact Online debtor
- Add all matched entries to the mapping table
- Flag any Zoho Books customers without an Exact debtor (these need debtor creation first)
- Mark example row as removed or replaced

### Out of scope
- Creating new debtors in Exact Online (separate action, outside this issue)
- Changing the mapping format or rules
- Updating automation code (mapping format is unchanged)

## Execution Steps

1. Export active customers from Zoho Books (customer_id, customer_name)
2. Export active debtors from Exact Online (debtor_code, debtor_name)
3. Match by customer name (or known correspondence)
4. Create feature branch: `feature/mapping-debtor-live-data`
5. Edit `mappings/debtor/debtor-mapping-rules.md`:
   - Remove the example row
   - Add one row per active customer with: customer_id, customer name, debtor code, debtor name, Status=Active, added date
6. Open PR using config-catalog PR template
7. Fill in all sections:
   - **Affected configuration objects:** debtor mapping table
   - **Downstream coordination:** No automation code change needed — mapping format unchanged, only data populated
   - **Validation performed:** Cross-checked Zoho Books customer list against Exact Online debtor list
8. Finance Lead reviews data accuracy
9. Merge after approval
10. Close this issue with PR link

## Validation Method

- Every active Zoho Books customer that generates invoices has a row in the mapping table
- Every debtor code in the table exists as an active debtor in Exact Online
- No duplicate customer_id entries
- No duplicate debtor code entries (one debtor per customer)

## Rollback Method

Revert the PR commit. The example row returns. No production impact — sync automation is not yet live.

## Evidence Required at Closure

- [ ] PR link with completed template
- [ ] Approval from Finance Lead on the PR
- [ ] Number of customers mapped (documented in PR description)
- [ ] List of unmapped customers (if any) with explanation
- [ ] Merged to main

## Acceptance Criteria

- [ ] All active Zoho Books customers with invoice history have a mapping entry
- [ ] All debtor codes verified against Exact Online
- [ ] Example row removed
- [ ] Finance Lead approved the PR
- [ ] PR merged to main
- [ ] Issue closed with PR link
- [ ] Any unmapped customers documented as follow-up issues

## Notes

This is the first pilot issue. It tests the full governed flow: issue → branch → PR → review → merge. Document any friction or gaps as improvement issues.
