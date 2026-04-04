# Journal Entry Templates

## Purpose
Predefined journal entry templates for recurring and standard entries in Exact Online.

## Recurring Monthly Entries

### Template: Monthly Accruals
| Line | GL account | Description | Debit | Credit |
|---|---|---|---|---|
| 1 | 4980 | Overlopende activa | XXX | |
| 2 | 8XXX | [Relevant revenue/cost account] | | XXX |

**Frequency:** Monthly
**Reversal:** Auto-reverse in next period
**Approval:** Finance Lead

### Template: Monthly Depreciation
| Line | GL account | Description | Debit | Credit |
|---|---|---|---|---|
| 1 | 4400 | Afschrijving materiële vaste activa | XXX | |
| 2 | 0XXX | Cumul. afschrijving [asset category] | | XXX |

**Frequency:** Monthly (via Exact Online depreciation run)
**Approval:** Finance Lead

### Template: Prepaid Expenses Release
| Line | GL account | Description | Debit | Credit |
|---|---|---|---|---|
| 1 | 4XXX | [Expense account] | XXX | |
| 2 | 1300 | Vooruitbetaalde kosten | | XXX |

**Frequency:** Monthly
**Approval:** Finance Lead

## Change Process
1. Template changes require Finance Lead approval
2. Update this document
3. Update recurring entry in Exact Online
4. Verify first posting after change
