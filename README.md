# Finance Configuration Catalog

**Owner:** Finance Lead

Authoritative source for finance configuration data: mapping tables, control matrix, exception definitions, journal templates, fixed asset rules, and close registers. This repository does not contain code or governance documentation.

## Structure

```
mappings/
├── sales-invoice/   — Sales invoice field mappings (Zoho Books → Exact)
├── debtor/          — Customer to debtor mapping rules
├── vat/             — VAT rate to VAT code mappings
└── account/         — Product category to GL account mappings

controls/            — Control matrix (authoritative register: FINANCE_CONTROL_MATRIX.md)
journals/            — Recurring journal entry templates
fixed-assets/        — Fixed asset rules, thresholds, depreciation methods
exceptions/          — Exception category definitions and severity levels
close-checklists/    — Close checklist register (completed periods)
```

## Key Documents

| Document | Purpose |
|---|---|
| [FINANCE_CONTROL_MATRIX.md](controls/FINANCE_CONTROL_MATRIX.md) | Authoritative register for all 26 finance controls |
| [exception-catalog.md](exceptions/exception-catalog.md) | Exception categories, severities, aging rules |
| [sales-invoice-field-mapping.md](mappings/sales-invoice/sales-invoice-field-mapping.md) | Zoho Books → Exact field mapping |

## Pull Request Template

This repo uses a lightly specialized PR template that prompts for affected configuration objects (mapping IDs, control IDs, journal templates) and downstream coordination with finance-automation. The specialization exists because config changes directly affect runtime behavior and must be coordinated with code updates.

## Change Rules

- All changes require Finance Lead approval via PR review
- VAT and tax-related changes also require CFO review
- Mapping changes must be coordinated with `finance-automation` code updates
- Control matrix changes require documented justification

## Consumed By

| Consumer | What it reads |
|---|---|
| finance-automation | Mapping tables, validation rules, exception categories |
| finance-runbooks | Control matrix, exception catalog, journal templates |
| finance-governance | References control matrix (via pointer, not copy) |
