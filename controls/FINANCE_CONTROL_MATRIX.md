# Finance Control Matrix

**Owner:** Finance Lead
**Version:** v2.0 — 2026-04-04
**Status:** Active

This is the authoritative register for all finance domain controls. All control references in other repositories point here.

---

## Sales Invoice Controls

### CTRL-SI-001 — Sync Completeness

| Attribute | Value |
|---|---|
| **Objective** | Ensure all sales invoices from Zoho Books are synced to Exact Online |
| **Type** | Detective |
| **Trigger / Frequency** | Daily (automated sync report) |
| **Input** | Zoho Books invoice count + Exact Online posted count |
| **Control action** | Compare counts. Any delta triggers investigation. |
| **Owner** | Technical Lead (detection), Finance Lead (resolution) |
| **Evidence** | Sync report with counts, timestamps, and delta |
| **Exception handling** | Log missing invoices as exception EX-SI. Investigate within 1 BD. |
| **Remediation** | Re-trigger sync for failed items. If structural: raise change request. |

### CTRL-SI-002 — Mapping Validation

| Attribute | Value |
|---|---|
| **Objective** | Prevent incorrectly mapped invoices from posting to Exact |
| **Type** | Preventive |
| **Trigger / Frequency** | Per transaction (before posting) |
| **Input** | Invoice data from Zoho Books + mapping tables from finance-config-catalog |
| **Control action** | Validate debtor, VAT code, GL account, and currency against mapping tables. Reject on any failure. |
| **Owner** | Technical Lead (automated), Finance Lead (exception resolution) |
| **Evidence** | Validation log per invoice (pass/fail per rule V-01 to V-08) |
| **Exception handling** | Failed validations logged as exception EX-SI. Invoice not posted until resolved. |
| **Remediation** | Update mapping table or correct source data. Re-validate and post. |

### CTRL-SI-003 — Debtor Consistency

| Attribute | Value |
|---|---|
| **Objective** | Ensure debtor records are consistent between Zoho Books and Exact Online |
| **Type** | Detective |
| **Trigger / Frequency** | Weekly |
| **Input** | Debtor list from Zoho Books + debtor list from Exact Online |
| **Control action** | Compare active debtors. Flag unmapped or inconsistent records. |
| **Owner** | Finance Lead |
| **Evidence** | Debtor comparison report |
| **Exception handling** | Unmapped debtors logged as exception. New debtors added to mapping table. |
| **Remediation** | Update debtor mapping in finance-config-catalog. Verify sync for affected invoices. |

### CTRL-SI-004 — Duplicate Detection

| Attribute | Value |
|---|---|
| **Objective** | Prevent duplicate sales invoices from being posted to Exact Online |
| **Type** | Preventive |
| **Trigger / Frequency** | Per transaction (before posting) |
| **Input** | Invoice number (with ZB- prefix) |
| **Control action** | Check if invoice reference already exists in Exact. Reject if duplicate. |
| **Owner** | Technical Lead (automated) |
| **Evidence** | Duplicate check log |
| **Exception handling** | Duplicate flagged, invoice not posted. Finance Lead investigates. |
| **Remediation** | Determine if true duplicate (discard) or numbering issue (correct and re-process). |

### CTRL-SI-005 — VAT Code Validation

| Attribute | Value |
|---|---|
| **Objective** | Ensure correct VAT codes on all sales invoices entering Exact |
| **Type** | Preventive |
| **Trigger / Frequency** | Per transaction (before posting) |
| **Input** | Tax percentage from Zoho Books + VAT mapping table |
| **Control action** | Map tax percentage to Exact VAT code. Reject if no valid mapping exists. |
| **Owner** | Technical Lead (automated), Finance Lead (mapping maintenance) |
| **Evidence** | VAT validation log per invoice |
| **Exception handling** | Unmapped VAT percentage logged as exception. Invoice held until resolved. |
| **Remediation** | Add VAT mapping or correct source data. Finance Lead approval required for new VAT mappings. |

---

## Purchase Controls

### CTRL-PU-001 — Invoice Completeness

| Attribute | Value |
|---|---|
| **Objective** | Ensure all purchase invoices are processed in Exact Online |
| **Type** | Detective |
| **Trigger / Frequency** | Weekly |
| **Input** | Purchase invoice register in Exact Online |
| **Control action** | Review for unprocessed invoices, follow up on outstanding items |
| **Owner** | Finance Lead |
| **Evidence** | Purchase processing status report |
| **Exception handling** | Unprocessed invoices logged. Investigate reason for delay. |
| **Remediation** | Process outstanding invoices. If systemic: raise improvement issue. |

### CTRL-PU-002 — Invoice Approval

| Attribute | Value |
|---|---|
| **Objective** | Ensure all purchase invoices are approved before payment |
| **Type** | Preventive |
| **Trigger / Frequency** | Per transaction |
| **Input** | Purchase invoice in Exact Online |
| **Control action** | Verify approval workflow completed before payment processing |
| **Owner** | Finance Lead |
| **Evidence** | Approval audit trail in Exact Online |
| **Exception handling** | Unapproved invoices flagged. Payment blocked until approved. |
| **Remediation** | Obtain approval or reject invoice. |

### CTRL-PU-003 — Creditor Review

| Attribute | Value |
|---|---|
| **Objective** | Identify aged or unusual creditor balances |
| **Type** | Detective |
| **Trigger / Frequency** | Monthly |
| **Input** | Creditor aging report from Exact Online |
| **Control action** | Review balances > 60 days. Investigate unusual amounts or suppliers. |
| **Owner** | Finance Lead |
| **Evidence** | Reviewed aging report with notes |
| **Exception handling** | Unusual items logged for investigation. |
| **Remediation** | Follow up with suppliers. Write off if appropriate (Finance Lead + CFO approval). |

---

## Bank Controls

### CTRL-BK-001 — Import Completeness

| Attribute | Value |
|---|---|
| **Objective** | Ensure all bank statements are imported into Exact Online |
| **Type** | Detective |
| **Trigger / Frequency** | Daily |
| **Input** | Bank portal statement dates vs Exact Online import dates |
| **Control action** | Verify latest import date matches latest available statement |
| **Owner** | Finance Lead |
| **Evidence** | Import log with dates |
| **Exception handling** | Missing statements flagged. Import manually if automated feed fails. |
| **Remediation** | Re-import missing statements. If feed issue: raise incident. |

### CTRL-BK-002 — Matching Completeness

| Attribute | Value |
|---|---|
| **Objective** | Ensure all bank transactions are matched to accounting entries |
| **Type** | Detective |
| **Trigger / Frequency** | Weekly |
| **Input** | Unmatched transaction list from Exact Online |
| **Control action** | Review and match unmatched items. Document items that cannot be matched. |
| **Owner** | Finance Lead |
| **Evidence** | Matching status report |
| **Exception handling** | Persistently unmatched items logged as exception. |
| **Remediation** | Match to existing entry or create new entry with documentation. |

### CTRL-BK-003 — Balance Reconciliation

| Attribute | Value |
|---|---|
| **Objective** | Ensure Exact Online bank balance matches actual bank statement balance |
| **Type** | Detective |
| **Trigger / Frequency** | Monthly |
| **Input** | Exact Online GL bank balance + bank statement balance |
| **Control action** | Reconcile balances. Document all reconciling items. |
| **Owner** | Finance Lead |
| **Evidence** | Completed reconciliation (use reconciliation template) |
| **Exception handling** | Unexplained differences logged. Investigate before close. |
| **Remediation** | Post adjusting entries or correct matching. Finance Lead approval. |

---

## Journal Controls

### CTRL-JN-001 — Entry Approval

| Attribute | Value |
|---|---|
| **Objective** | Ensure all manual journal entries are approved before posting |
| **Type** | Preventive |
| **Trigger / Frequency** | Per transaction |
| **Input** | Journal entry with supporting documentation |
| **Control action** | Finance Lead reviews and approves each manual journal before posting |
| **Owner** | Finance Lead |
| **Evidence** | Approval record per journal entry |
| **Exception handling** | Unapproved journals may not be posted. |
| **Remediation** | Obtain approval or withdraw entry. |

### CTRL-JN-002 — Recurring Verification

| Attribute | Value |
|---|---|
| **Objective** | Ensure recurring journal entries match approved templates |
| **Type** | Detective |
| **Trigger / Frequency** | Monthly |
| **Input** | Posted recurring entries vs journal templates (finance-config-catalog/journals/) |
| **Control action** | Compare posted amounts and accounts to template. Flag deviations. |
| **Owner** | Finance Lead |
| **Evidence** | Template comparison report |
| **Exception handling** | Deviations logged. Finance Lead investigates. |
| **Remediation** | Correct entry or update template (with approval). |

### CTRL-JN-003 — Entry Documentation

| Attribute | Value |
|---|---|
| **Objective** | Ensure every journal entry has adequate supporting documentation |
| **Type** | Preventive |
| **Trigger / Frequency** | Per transaction |
| **Input** | Journal entry in Exact Online |
| **Control action** | Verify supporting documentation is attached or referenced before posting |
| **Owner** | Finance Lead |
| **Evidence** | Journal entry with attached support |
| **Exception handling** | Entries without support may not be posted. |
| **Remediation** | Obtain supporting documentation before posting. |

---

## Fixed Asset Controls

### CTRL-FA-001 — Register Completeness

| Attribute | Value |
|---|---|
| **Objective** | Ensure the asset register in Exact Online reflects all known assets |
| **Type** | Detective |
| **Trigger / Frequency** | Monthly |
| **Input** | Asset register from Exact Online |
| **Control action** | Review register against known additions, disposals, and physical inventory |
| **Owner** | Finance Lead |
| **Evidence** | Reviewed asset register with notes |
| **Exception handling** | Missing or unrecognized assets logged for investigation. |
| **Remediation** | Add missing assets or dispose of phantom assets (with approval). |

### CTRL-FA-002 — Depreciation Review

| Attribute | Value |
|---|---|
| **Objective** | Ensure depreciation calculations are reasonable and correct |
| **Type** | Detective |
| **Trigger / Frequency** | Monthly |
| **Input** | Depreciation calculation output from Exact Online |
| **Control action** | Preview depreciation run. Compare to expected amounts. Review for reasonableness. |
| **Owner** | Finance Lead |
| **Evidence** | Depreciation preview report with review notes |
| **Exception handling** | Unreasonable amounts flagged. Do not post until investigated. |
| **Remediation** | Correct asset data or depreciation parameters. Re-run preview. |

### CTRL-FA-003 — Addition/Disposal Approval

| Attribute | Value |
|---|---|
| **Objective** | Ensure all asset additions and disposals are properly authorized |
| **Type** | Preventive |
| **Trigger / Frequency** | Per transaction |
| **Input** | Asset addition or disposal request |
| **Control action** | Finance Lead approves before processing in Exact Online |
| **Owner** | Finance Lead |
| **Evidence** | Approval record for each addition/disposal |
| **Exception handling** | Unapproved additions/disposals may not be processed. |
| **Remediation** | Obtain approval or reject request. |

---

## VAT/Tax Controls

### CTRL-VT-001 — Return Reconciliation

| Attribute | Value |
|---|---|
| **Objective** | Ensure VAT return amounts reconcile to the general ledger |
| **Type** | Detective |
| **Trigger / Frequency** | Monthly (preparation), Quarterly (filing) |
| **Input** | VAT return data + GL VAT account balances from Exact Online |
| **Control action** | Reconcile VAT return amounts to GL. Document all differences. |
| **Owner** | Finance Lead |
| **Evidence** | VAT reconciliation (use reconciliation template) |
| **Exception handling** | Unexplained differences investigated before filing. |
| **Remediation** | Post correcting entries or adjust return. Finance Lead + CFO approval for material adjustments. |

### CTRL-VT-002 — Code Usage Review

| Attribute | Value |
|---|---|
| **Objective** | Ensure transactions are coded with correct VAT codes |
| **Type** | Detective |
| **Trigger / Frequency** | Monthly |
| **Input** | Transaction listing by VAT code from Exact Online |
| **Control action** | Review transaction sample per VAT code for correctness |
| **Owner** | Finance Lead |
| **Evidence** | Reviewed transaction sample with notes |
| **Exception handling** | Incorrectly coded transactions flagged for correction. |
| **Remediation** | Post correcting entries. If systemic: update mapping rules and raise change request. |

### CTRL-VT-003 — Reverse Charge Verification

| Attribute | Value |
|---|---|
| **Objective** | Ensure reverse charge VAT is correctly applied where required |
| **Type** | Detective |
| **Trigger / Frequency** | Monthly |
| **Input** | Reverse charge transactions from Exact Online |
| **Control action** | Verify reverse charge applied to correct supplier/transaction types |
| **Owner** | Finance Lead |
| **Evidence** | Reverse charge review report |
| **Exception handling** | Missing or incorrect reverse charge flagged. |
| **Remediation** | Post correcting entries. Update supplier or VAT settings. |

---

## Close Controls

### CTRL-MC-001 — Checklist Completion

| Attribute | Value |
|---|---|
| **Objective** | Ensure all close tasks are completed before period close |
| **Type** | Detective |
| **Trigger / Frequency** | Monthly (during close) |
| **Input** | Close checklist for the period |
| **Control action** | Verify every task is marked complete with evidence before final close |
| **Owner** | Finance Lead |
| **Evidence** | Completed close checklist |
| **Exception handling** | Incomplete items must be resolved or deferred (with documented justification). |
| **Remediation** | Complete outstanding tasks or document deferral reason. |

### CTRL-MC-002 — Balance Sheet Review

| Attribute | Value |
|---|---|
| **Objective** | Ensure all balance sheet accounts are reviewed and balances are explained |
| **Type** | Detective |
| **Trigger / Frequency** | Monthly (Phase 3 of close) |
| **Input** | Trial balance from Exact Online |
| **Control action** | Review each BS account. Confirm balance is expected and supported. |
| **Owner** | Finance Lead |
| **Evidence** | BS review notes per account |
| **Exception handling** | Unexplained balances flagged. Investigate before close. |
| **Remediation** | Post adjusting entries or obtain explanation. |

### CTRL-MC-003 — P&L Variance Analysis

| Attribute | Value |
|---|---|
| **Objective** | Identify and explain material P&L variances |
| **Type** | Detective |
| **Trigger / Frequency** | Monthly (Phase 3 of close) |
| **Input** | P&L actual vs budget, P&L actual vs prior period |
| **Control action** | Identify variances exceeding materiality threshold. Document explanations. |
| **Owner** | Finance Lead |
| **Evidence** | Variance analysis with explanations |
| **Exception handling** | Unexplained material variances escalated to CFO. |
| **Remediation** | Investigate, post correcting entries if needed, document root cause. |

### CTRL-MC-004 — Period Close Approval

| Attribute | Value |
|---|---|
| **Objective** | Ensure period close is explicitly approved before execution |
| **Type** | Preventive |
| **Trigger / Frequency** | Monthly (Phase 4 of close) |
| **Input** | Close package (checklist, reconciliations, variance analysis, control results) |
| **Control action** | Finance Lead and CFO review close package and approve period close |
| **Owner** | Finance Lead + CFO |
| **Evidence** | Signed approval (name + date) |
| **Exception handling** | Close does not proceed without approval. Objections documented and addressed. |
| **Remediation** | Address objections, re-submit for approval. |

---

## Exception Controls

### CTRL-EX-001 — Aging Review

| Attribute | Value |
|---|---|
| **Objective** | Prevent exceptions from aging without attention |
| **Type** | Detective |
| **Trigger / Frequency** | Weekly |
| **Input** | Open exception register (GitHub issues) |
| **Control action** | Review all exceptions open > 5 business days. Escalate if needed. |
| **Owner** | Finance Lead |
| **Evidence** | Exception aging report with actions taken |
| **Exception handling** | Exceptions > 10 BD escalated. Owner reassignment if needed. |
| **Remediation** | Resolve, reassign, or escalate. Document actions taken. |

### CTRL-EX-002 — Resolution Documentation

| Attribute | Value |
|---|---|
| **Objective** | Ensure every resolved exception has documented resolution |
| **Type** | Preventive |
| **Trigger / Frequency** | Per resolution |
| **Input** | Resolved exception (GitHub issue) |
| **Control action** | Verify resolution includes: root cause, actions taken, preventive measures, evidence |
| **Owner** | Finance Lead |
| **Evidence** | Completed exception analysis (use exception analysis template) |
| **Exception handling** | Exceptions may not be closed without documented resolution. |
| **Remediation** | Complete documentation before closing. |

---

## Assessment Schedule

| Control area | Assessment frequency |
|---|---|
| Sales invoice (CTRL-SI-*) | Monthly |
| Purchase (CTRL-PU-*) | Monthly |
| Bank (CTRL-BK-*) | Monthly |
| Journal (CTRL-JN-*) | Monthly |
| Fixed asset (CTRL-FA-*) | Quarterly |
| VAT/tax (CTRL-VT-*) | Quarterly |
| Close (CTRL-MC-*) | Monthly |
| Exception (CTRL-EX-*) | Monthly |

## Maintenance

Changes to this matrix require:
1. Change request in GitHub
2. Finance Lead approval
3. CFO approval if control is added, removed, or materially changed
4. Update to this document
5. Communication to affected owners
