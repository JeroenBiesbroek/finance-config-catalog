# Exception Catalog

## Purpose
Defines the categories, severities, and standard handling procedures for finance exceptions.

## Exception Categories

| Category | Code | Description | Default owner |
|---|---|---|---|
| Sales Invoice Sync | EX-SI | Exceptions from Zoho Books to Exact Online sync | Technical Lead |
| Purchase Processing | EX-PU | Issues with purchase invoice processing | Finance Lead |
| Bank Matching | EX-BK | Unmatched or problematic bank transactions | Finance Lead |
| Journal Entry | EX-JN | Issues with journal entries | Finance Lead |
| Fixed Asset | EX-FA | Asset register or depreciation issues | Finance Lead |
| VAT/Tax | EX-VT | VAT-related discrepancies | Finance Lead |
| Close | EX-MC | Issues discovered during month-end close | Finance Lead |
| System | EX-SY | Technical/system failures | Technical Lead |

## Severity Levels

| Severity | Definition | Response time | Escalation |
|---|---|---|---|
| Critical | Financial data at risk | < 4 hours | Finance Lead + CFO |
| High | Operations impacted, no data loss | < 1 business day | Finance Lead |
| Medium | Needs attention, workaround available | < 3 business days | — |
| Low | Minor, no operational impact | < 5 business days | — |

## Aging Rules

- Exceptions open > 5 business days: reviewed by Finance Lead (CTRL-EX-001)
- Exceptions open > 10 business days: escalated
- All resolved exceptions must have documented resolution (CTRL-EX-002)

## Standard Exception Flow

```
Detected → Logged → Triaged → Assigned → Investigated → Resolved → Documented
                                                             │
                                                             └→ Preventive action identified
```
