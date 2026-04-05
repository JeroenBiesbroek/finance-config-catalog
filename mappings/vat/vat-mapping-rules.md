# VAT Mapping Rules — Zoho Books Tax Rates to Exact Online VAT Codes

## Mapping Version
v2.1 — 2026-04-05

## Source Extract Date
2026-04-05 (Zoho Books tax settings + Exact Online BTW-overzicht Q1 2026)

## Rules

1. Every tax percentage used in Zoho Books must map to a valid VAT code in Exact Online
2. The VAT code must exist in the Exact Online administration before mapping
3. Changes to VAT mappings require Finance Lead approval
4. VAT-sensitive changes also require CFO review

## Mapping Table

| Zoho Books tax name | Zoho Books tax_percentage | Exact Online VAT code | Exact Online description | GL account | Status | Verified |
|---|---|---|---|---|---|---|
| BTW hoog | 21 | 1A | Leveringen/diensten belast met hoog tarief | 8000 | Active | Yes — Q1 2026 confirmed |
| BTW laag | 9 | 1B | Leveringen/diensten belast met laag tarief | 8010 | Active | Yes — code exists, not used in Q1 2026 |
| BTW vrijgesteld | 0 | — | — | — | Pending Thijs | No — see follow-up below |
| zonder BTW | 0 | — | — | — | Pending Thijs | No — see follow-up below |
| EU verlegd | — | 4A | BTW verlegd EU (verkoop) | 8040 | Active | Yes — activated per Finance Lead decision. Zoho Books tax rate must be created. |
| Export buiten EU | — | 5 | Export buiten EU | 8110 | Active | Yes — activated per Finance Lead decision. Zoho Books tax rate must be created. |

## Decisions Applied

| # | Decision | Applied by | Date |
|---|---|---|---|
| 1 | Two 0% rates: Thijs must investigate and decide correct VAT code mapping | Finance Lead | 2026-04-05 |
| 2 | EU reverse charge (4A) and Export (5): activated. Matching Zoho Books tax rates must be created. | Finance Lead | 2026-04-05 |

## Follow-up Actions — Owner: thijs@powercrumbs.com

| # | Action | Priority |
|---|---|---|
| 1 | Investigate BTW vrijgesteld vs zonder BTW: determine correct Exact Online VAT codes for each. Update this mapping table via PR. | High |
| 2 | Create "EU verlegd" tax rate in Zoho Books (matching code 4A in Exact) | Medium |
| 3 | Create "Export buiten EU" tax rate in Zoho Books (matching code 5 in Exact) | Medium |

## Verification Summary

| Check | Result |
|---|---|
| Zoho Books active tax rates | 4 (BTW hoog 21%, BTW laag 9%, BTW vrijgesteld 0%, zonder BTW 0%) |
| Exact Online VAT codes with Q1 2026 activity | 1A (sales), 4B (EU purchase), 5B (input tax) |
| Mappings fully verified | 2 (21% → 1A, 9% → 1B) |
| Mappings activated (Zoho rate to be created) | 2 (EU reverse charge 4A, Export 5) |
| Mappings pending Thijs investigation | 2 (BTW vrijgesteld 0%, zonder BTW 0%) |
| Finance Lead decisions remaining | 0 |

## Validation Rule
- V-02: Every `tax_percentage` on a Zoho Books invoice line must match an entry in this table
- Invoices with unmapped tax rates are rejected and logged as exceptions

## Change Process
1. Change request in GitHub with `control:high-impact` label
2. Update this table
3. Update automation code if needed
4. Test with sample invoices
5. Finance Lead + CFO approval required
