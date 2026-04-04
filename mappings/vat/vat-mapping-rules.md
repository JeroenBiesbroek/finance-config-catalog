# VAT Mapping Rules — Zoho Books Tax Rates to Exact Online VAT Codes

## Mapping Version
v1.0 — 2026-04-04

## Rules

1. Every tax percentage used in Zoho Books must map to a valid VAT code in Exact Online
2. The VAT code must exist in the Exact Online administration before mapping
3. Changes to VAT mappings require Finance Lead approval
4. VAT-sensitive changes also require CFO review

## Mapping Table

| Zoho Books tax_percentage | Description | Exact Online VAT code | Exact Online description | Status |
|---|---|---|---|---|
| 21 | Standard rate (21%) | 1A | BTW 21% verkoop binnenland | Active |
| 9 | Reduced rate (9%) | 1B | BTW 9% verkoop binnenland | Active |
| 0 | Zero rate / exempt | 0 | Geen BTW | Active |
| — | Reverse charge (EU) | 4A | BTW verlegd EU | Active |
| — | Export (outside EU) | 5 | Export buiten EU | Active |

> **Note:** Update this table when new VAT rates or codes are introduced. All changes require Finance Lead + CFO approval.

## Validation Rule
- V-02: Every `tax_percentage` on a Zoho Books invoice line must match an entry in this table
- Invoices with unmapped tax rates are rejected and logged as exceptions

## Change Process
1. Change request in GitHub with `control:high-impact` label
2. Update this table
3. Update automation code if needed
4. Test with sample invoices
5. Finance Lead + CFO approval required
