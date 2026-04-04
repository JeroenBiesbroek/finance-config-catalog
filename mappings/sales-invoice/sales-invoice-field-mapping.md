# Sales Invoice Field Mapping — Zoho Books to Exact Online

## Mapping Version
v1.0 — 2026-04-04

## Invoice Header Mapping

| # | Zoho Books field | Exact Online field | Mapping type | Rule | Notes |
|---|---|---|---|---|---|
| 1 | `customer_id` | Debtor code | Lookup | Via debtor mapping table | Must exist before sync |
| 2 | `invoice_number` | Invoice reference | Transform | Prefix with "ZB-" | e.g., ZB-INV-001 |
| 3 | `invoice_date` | Invoice date | Direct | YYYY-MM-DD | Must be in open period |
| 4 | `due_date` | Due date | Direct | YYYY-MM-DD | |
| 5 | `currency_code` | Currency | Lookup | Via currency mapping | Default: EUR |
| 6 | `reference_number` | Description | Direct | — | Optional |
| 7 | `total` | — | Validation only | Used for V-06 check | Not mapped to a field |

## Invoice Line Mapping

| # | Zoho Books field | Exact Online field | Mapping type | Rule | Notes |
|---|---|---|---|---|---|
| 1 | `description` | Line description | Direct | Truncate to 60 chars | |
| 2 | `item_total` | Line amount | Direct | — | |
| 3 | `tax_percentage` | VAT code | Lookup | Via VAT mapping table | |
| 4 | `quantity` | Quantity | Direct | Default: 1 | |
| 5 | `rate` | Unit price | Direct | — | |
| 6 | `product_category` | GL account | Lookup | Via account mapping table | |

## Mapping Tables

### Debtor Mapping
Located at: `finance-config-catalog/mappings/debtor/debtor-mapping-rules.md`

### VAT Mapping
Located at: `finance-config-catalog/mappings/vat/vat-mapping-rules.md`

### Account Mapping
Located at: `finance-config-catalog/mappings/account/account-mapping-rules.md`

## Change Process

Any change to this mapping requires:
1. Change request in GitHub
2. Update to this document
3. Corresponding code update in finance-automation
4. Test evidence
5. Finance Lead approval
