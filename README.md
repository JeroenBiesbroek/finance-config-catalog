# Finance Configuration Catalog

**Owner:** Finance Lead

This repository catalogs finance mappings, controls, exception definitions, close registers, and configuration references.

## Structure

```
mappings/
├── sales-invoice/   # Sales invoice field mappings
├── debtor/          # Customer to debtor mapping rules
├── vat/             # VAT rate to VAT code mappings
└── account/         # Product category to GL account mappings

controls/            # Control matrix (authoritative register)
journals/            # Journal entry templates
fixed-assets/        # Fixed asset rules and policies
exceptions/          # Exception category definitions
close-checklists/    # Close checklist register
```

## Rules
- All changes require Finance Lead approval via PR review
- VAT and tax-related changes also require CFO review
- If a catalog entry is wrong, fix it immediately
