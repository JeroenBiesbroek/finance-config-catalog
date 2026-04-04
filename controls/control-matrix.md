# Control Matrix — Finance Domain

## Version
v1.0 — 2026-04-04

## Control Register

| Control ID | Area | Control name | Type | Frequency | Owner | Description | Last assessed | Result |
|---|---|---|---|---|---|---|---|---|
| CTRL-SI-001 | Sales Invoices | Sync completeness | Detective | Daily | Technical Lead | Verify all Zoho Books invoices synced to Exact | — | — |
| CTRL-SI-002 | Sales Invoices | Mapping validation | Preventive | Per txn | Technical Lead | Validate field mappings before posting | — | — |
| CTRL-SI-003 | Sales Invoices | Debtor consistency | Detective | Weekly | Finance Lead | Verify debtor records match across systems | — | — |
| CTRL-SI-004 | Sales Invoices | Duplicate detection | Preventive | Per txn | Technical Lead | Check for duplicate invoice numbers | — | — |
| CTRL-SI-005 | Sales Invoices | VAT code validation | Preventive | Per txn | Technical Lead | Validate VAT codes against allowed values | — | — |
| CTRL-PU-001 | Purchases | Invoice completeness | Detective | Weekly | Finance Lead | Verify all purchase invoices are processed | — | — |
| CTRL-PU-002 | Purchases | Invoice approval | Preventive | Per txn | Finance Lead | All purchase invoices require approval | — | — |
| CTRL-PU-003 | Purchases | Creditor review | Detective | Monthly | Finance Lead | Review aged creditor balances | — | — |
| CTRL-BK-001 | Bank | Import completeness | Detective | Daily | Finance Lead | Verify all bank statements imported | — | — |
| CTRL-BK-002 | Bank | Matching completeness | Detective | Weekly | Finance Lead | Review unmatched bank transactions | — | — |
| CTRL-BK-003 | Bank | Balance reconciliation | Detective | Monthly | Finance Lead | Reconcile Exact bank balance to statements | — | — |
| CTRL-JN-001 | Journals | Entry approval | Preventive | Per txn | Finance Lead | All manual journals require approval | — | — |
| CTRL-JN-002 | Journals | Recurring verification | Detective | Monthly | Finance Lead | Verify recurring entries match template | — | — |
| CTRL-JN-003 | Journals | Entry documentation | Preventive | Per txn | Finance Lead | Every journal must have support | — | — |
| CTRL-FA-001 | Fixed Assets | Register completeness | Detective | Monthly | Finance Lead | Verify asset register matches known assets | — | — |
| CTRL-FA-002 | Fixed Assets | Depreciation review | Detective | Monthly | Finance Lead | Review depreciation for reasonableness | — | — |
| CTRL-FA-003 | Fixed Assets | Addition/disposal approval | Preventive | Per txn | Finance Lead | Additions and disposals require approval | — | — |
| CTRL-VT-001 | VAT/Tax | Return reconciliation | Detective | Monthly/Quarterly | Finance Lead | Reconcile VAT return to GL | — | — |
| CTRL-VT-002 | VAT/Tax | Code usage review | Detective | Monthly | Finance Lead | Review transactions for correct VAT codes | — | — |
| CTRL-VT-003 | VAT/Tax | Reverse charge verification | Detective | Monthly | Finance Lead | Verify reverse charge processing | — | — |
| CTRL-MC-001 | Close | Checklist completion | Detective | Monthly | Finance Lead | All close items completed before period close | — | — |
| CTRL-MC-002 | Close | Balance sheet review | Detective | Monthly | Finance Lead | All BS accounts reviewed and explained | — | — |
| CTRL-MC-003 | Close | P&L variance analysis | Detective | Monthly | Finance Lead | Material variances identified and explained | — | — |
| CTRL-MC-004 | Close | Period close approval | Preventive | Monthly | Finance Lead + CFO | Period close requires explicit approval | — | — |
| CTRL-EX-001 | Exceptions | Aging review | Detective | Weekly | Finance Lead | Review exceptions older than 5 BD | — | — |
| CTRL-EX-002 | Exceptions | Resolution documentation | Preventive | Per resolution | Finance Lead | Every resolution must be documented | — | — |

## Assessment Schedule

- Sales invoice controls: Monthly
- Purchase controls: Monthly
- Bank controls: Monthly
- Journal controls: Monthly
- Fixed asset controls: Quarterly
- VAT/tax controls: Quarterly
- Close controls: Monthly
- Exception controls: Monthly

## Maintenance

This matrix is the authoritative register. It is maintained in `finance-config-catalog` and referenced by the control framework in `finance-product`.

Changes follow the standard change process with Finance Lead approval.
