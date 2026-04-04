# VAT Mapping Rules — Zoho Books Tax Rates to Exact Online VAT Codes

## Mapping Version
v2.0 — 2026-04-05

## Source Extract Date
2026-04-05 (Zoho Books tax settings + Exact Online BTW-overzicht Q1 2026)

## Rules

1. Every tax percentage used in Zoho Books must map to a valid VAT code in Exact Online
2. The VAT code must exist in the Exact Online administration before mapping
3. Changes to VAT mappings require Finance Lead approval
4. VAT-sensitive changes also require CFO review

## Mapping Table

| Zoho Books tax name | Zoho Books tax_percentage | Exact Online VAT code | Exact Online description | GL account | Status | Verified | Reviewer notes |
|---|---|---|---|---|---|---|---|
| BTW hoog | 21 | 1A | Leveringen/diensten belast met hoog tarief | 8000 | Active | Yes | Confirmed in Q1 2026 BTW-overzicht: grondslag 42.344,34 / btw 8.892,32. Primary sales VAT code. |
| BTW laag | 9 | 1B | Leveringen/diensten belast met laag tarief | 8010 | Active | Pending | Code exists in Exact (GL 8010). Not used in Q1 2026 BTW-overzicht. Verify if any invoices use 9% rate. |
| BTW vrijgesteld | 0 | 0 | Geen BTW / vrijgesteld | 8020 | Active | Pending | GL 8020 (nultarief) exists. Not used in Q1 2026. Verify if distinction from "zonder BTW" is needed for V-02. |
| zonder BTW | 0 | 0 | Geen BTW / vrijgesteld | 8020 | Active | Pending | Same 0% rate as "BTW vrijgesteld". Finance Lead must decide: same VAT code or different handling. |
| — | — | 4A | BTW verlegd EU (verkoop) | 8040 | Inactive | No | In original mapping but no matching Zoho Books tax rate. GL 8040 exists. Only activate when EU reverse charge sales invoices occur. |
| — | — | 5 | Export buiten EU | 8110 | Inactive | No | In original mapping but no matching Zoho Books tax rate. GL 8110 exists. Only activate when export invoices occur. |

## Verification Summary

| Check | Result |
|---|---|
| Zoho Books active tax rates | 4 (BTW hoog 21%, BTW laag 9%, BTW vrijgesteld 0%, zonder BTW 0%) |
| Exact Online VAT codes with Q1 2026 activity | 1A (sales), 4B (EU purchase), 5B (input tax) |
| Mappings fully verified against live data | 1 (21% → 1A) |
| Mappings structurally correct but unused in Q1 | 3 (9% → 1B, 0% exempt, 0% without) |
| Mappings without Zoho counterpart | 2 (EU reverse charge, export) — set to Inactive |

## Decisions Required (Finance Lead + CFO)

1. **Two 0% rates in Zoho Books**: "BTW vrijgesteld" and "zonder BTW" both map to 0%. Should they use the same Exact VAT code, or should "zonder BTW" use a different code (e.g., for non-taxable items vs exempt items)?
2. **EU reverse charge and export**: These exist in Exact Online (codes 4A/8040 and 5/8110) but have no Zoho Books tax rate counterpart. Are these needed for any current or planned invoicing?

## Validation Rule
- V-02: Every `tax_percentage` on a Zoho Books invoice line must match an entry in this table
- Invoices with unmapped tax rates are rejected and logged as exceptions

## Change Process
1. Change request in GitHub with `control:high-impact` label
2. Update this table
3. Update automation code if needed
4. Test with sample invoices
5. Finance Lead + CFO approval required
