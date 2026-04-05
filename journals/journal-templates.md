# Journal Entry Templates — Exact Online

## Version
v2.0 — 2026-04-05

## Source
GL accounts extracted from Exact Online administration 95001712 (Powercrumbs B.V.) on 2026-04-05. No recurring entries ("vaste boekingen") were configured in Exact Online — these templates are the first structured definition.

## Dagboek (Journal)
All monthly memorial entries use dagboek **80 - Memoriaal** unless otherwise specified.

---

## Template 1: Monthly Depreciation

**Purpose:** Post monthly depreciation for all fixed asset categories.
**Frequency:** Monthly (via Exact Online depreciation run: Financieel > Activa > Afschrijven)
**Dagboek:** 95 - Activamutaties
**Approval:** Finance Lead
**Method:** Use Exact Online built-in depreciation run (preview → review → post). Do NOT post manually.

### Expected GL accounts

| Asset category | Debit (expense) | Credit (cumulative) | Notes |
|---|---|---|---|
| Intellectueel eigendom | 4400* | 0145 | Cumulatieve afschrijving Intellectueel eigendom |
| Goodwill | 4400* | 0151 | Cumulatieve afschrijving Goodwill |
| Software / automatisering / AI | 4400* | 0155 | Cumulatieve afschrijvingen Software |
| Onderzoek en Ontwikkeling | 4400* | 0160 | Including 0160.01 (Zaandam) |
| Machines (Powerhub 1-6) | 4400* | 0220.01–0220.06 | Individual asset tracking |
| Powerbox | 4400* | 0220.30 | Cumulatieve afschrijving Powerbox |
| Inrichting | 4400* | 0281 | |
| Bedrijfsinventaris | 4400* | 0375 | |
| Kantoorinventaris | 4400* | 0385 | |
| Hard- en software | 4400* | 0391 | |
| Transport en vervoermiddelen | 4400* | 0430 | |

> *\*Note:* The exact 4400-level expense account depends on the asset group configuration in Exact Online. The depreciation run auto-selects the correct expense account. Verify the depreciation preview before posting.

### Control
- CTRL-FA-002: Review depreciation output for reasonableness before posting
- Compare total depreciation amount to prior month — flag deviations > 10%

---

## Template 2: Monthly Salary Accruals

**Purpose:** Accrue holiday pay (vakantiegeld) and 13th month reserves.
**Frequency:** Monthly
**Dagboek:** 80 - Memoriaal
**Approval:** Finance Lead
**Reversal:** No — these are cumulative reserves, not reversing accruals.

| Line | GL account | Description | Debit | Credit | Amount basis |
|---|---|---|---|---|---|
| 1 | 4050* | Reservering vakantiegeld (expense) | X | | 8% of gross salary |
| 2 | 1780 | Nog te betalen reservering vakantiegeld | | X | Balance sheet liability |
| 3 | 4050* | Reservering 13e maand (expense) | X | | 8.33% of gross salary |
| 4 | 1770 | Te betalen reservering 13e maand | | X | Balance sheet liability |
| 5 | 4050* | Werkgeverslasten over reserveringen | X | | ~20% of lines 1+3 |
| 6 | 1771 | Reservering werkgeverslasten 13e maand | | X | |
| 7 | 1781 | Nog te betalen reservering werkgeverskosten | | X | |

> *\*Note:* The exact 4050-level expense account for salary reserves must be confirmed by Finance Lead. Amounts depend on actual payroll data. Finance Lead fills in actual EUR amounts before first use.

### Assumptions
- Holiday pay accrual: 8% of gross monthly salary
- 13th month accrual: 8.33% (1/12) of gross monthly salary
- Employer charges: ~20% of base accrual (social premiums, pension)
- **These percentages and amounts must be verified by Finance Lead against actual payroll contracts**

### Control
- CTRL-JN-002: Compare posted amounts to this template each month

---

## Template 3: Monthly Cost Accruals

**Purpose:** Accrue known costs not yet invoiced (accountant, energy, telephone, bank, etc.).
**Frequency:** Monthly
**Dagboek:** 80 - Memoriaal
**Approval:** Finance Lead
**Reversal:** Reverse in next period when actual invoice is received.

| Line | GL account (credit) | GL account (debit) | Description | Estimated monthly amount |
|---|---|---|---|---|
| 1 | 1887 | 4030* | Nog te betalen accountantskosten | Finance Lead fills in |
| 2 | 1888 | 4020* | Nog te betalen energiekosten | Finance Lead fills in |
| 3 | 1886 | 4020* | Nog te betalen telefoonkosten | Finance Lead fills in |
| 4 | 1885 | 4590* | Nog te betalen bankkosten | Finance Lead fills in |
| 5 | 1884 | 4010* | Nog te betalen huurkosten | Finance Lead fills in |
| 6 | 1889 | 4XXX | Nog te betalen overig | Finance Lead fills in |

> *\*Note:* Debit expense GL accounts (4xxx) must be confirmed by Finance Lead against the chart of accounts. The credit accounts (18xx) are confirmed from Exact Online.

### Assumptions
- Only accrue if the cost is material and predictable
- Reverse the full accrual in the next period
- When the actual invoice arrives, book it normally — the reversal + actual invoice nets to the correct amount

### Control
- CTRL-JN-001: Each manual accrual journal requires Finance Lead approval
- CTRL-JN-003: Each entry must have documented support (estimate basis)

---

## Template 4: Revenue Recognition / Deferred Revenue

**Purpose:** Release prepaid revenue or accrue revenue earned but not yet invoiced.
**Frequency:** Monthly (when applicable)
**Dagboek:** 94 - Memoriaal uitgestelde omzet en kosten
**Approval:** Finance Lead

### 4a: Release prepaid (vooruitbetaald)
| Line | GL account | Description | Debit | Credit |
|---|---|---|---|---|
| 1 | 1450 | Vooruitbetaalde kosten | | X |
| 2 | 4XXX | [Relevant expense account] | X | |

### 4b: Accrue earned but unbilled revenue
| Line | GL account | Description | Debit | Credit |
|---|---|---|---|---|
| 1 | 1370 | Nog te factureren posten | X | |
| 2 | 8XXX | [Relevant revenue account] | | X |

### 4c: Mutatie onderhanden werk
| Line | GL account | Description | Debit | Credit |
|---|---|---|---|---|
| 1 | 1370 | Nog te factureren posten | X | |
| 2 | 8200 | Mutatie onderhanden werk | | X |

> Use 4a, 4b, or 4c as appropriate. Finance Lead determines which applies each period.

---

## Usage During Month-End Close

1. **Phase 2 — Controlled Close, step 2.1:** Post depreciation using Exact Online depreciation run (Template 1)
2. **Phase 2 — step 2.2:** Post salary accruals (Template 2) and cost accruals (Template 3)
3. **Phase 2 — step 2.3:** Reverse prior period cost accruals (reverse of Template 3)
4. **Phase 2 — step 2.4:** Post revenue adjustments if applicable (Template 4)
5. **Phase 2 — step 2.5:** Post any other manual journals with support

## First Close Preparation Required

Before the first governed close, Finance Lead must:
- [ ] Confirm or update the expense GL accounts marked with * in Templates 2 and 3
- [ ] Fill in estimated monthly amounts for Template 3 (cost accruals)
- [ ] Verify salary accrual percentages against actual payroll contracts
- [ ] Decide which Template 4 variants apply to current operations

## Change Process
1. Template changes require Finance Lead approval
2. Update this document
3. Update recurring entry in Exact Online (if using vaste boekingen)
4. Verify first posting after change
