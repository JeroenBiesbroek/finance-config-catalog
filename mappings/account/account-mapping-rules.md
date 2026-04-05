# Account Mapping Rules — Product Categories to GL Accounts

## Mapping Version
v2.1 — 2026-04-05

## Source Extract Date
2026-04-05 (Zoho Books items + Exact Online chart of accounts 8xxx range)

## Rules

1. Each product/service category in Zoho Books maps to a revenue GL account in Exact Online
2. The GL account must exist in the Exact Online chart of accounts
3. A default account is used when no specific category match is found
4. Changes require Finance Lead approval

## Mapping Table

| Product category (Zoho Books) | GL account (Exact Online) | Account description | Status | Verified |
|---|---|---|---|---|
| default | 8000 | Omzet binnenland hoog tarief | Active | Yes |
| consulting | 8800 | Omzet honorarium | Active | Yes |
| services | 8060 | Omzet services | Pending creation | No — GL 8060 must be created in Exact by Thijs |
| products | 8030 | Netto omzet | Active | Yes |
| subscriptions | 8070 | Omzet abonnementen | Pending creation | No — GL 8070 must be created in Exact by Thijs |
| biogas | 8050 | Omzet biogas premium | Active | Yes |
| wholesale | 8051 | Omzet wholesale | Active | Yes |
| groengas | 8052 | Omzet groengas | Active | Yes |
| powerbox-20 | 8053 | Verhuur powerbox 20 premium | Active | Yes |
| powerbox-10 | 8054 | Verhuur powerbox 10 premium | Active | Yes |
| transport | 8055 | Opbrengst transport premium | Active | Yes |
| subsidies-consultancy | 8056 | Opbrengst subsidies/consultancy | Active | Yes |
| overig | 8057 | Opbrengst overig | Active | Yes |

## Decisions Applied

| # | Decision | Applied by | Date |
|---|---|---|---|
| 1 | Services: new GL account 8060 "Omzet services" | Finance Lead | 2026-04-05 |
| 2 | Subscriptions: new GL account 8070 "Omzet abonnementen" | Finance Lead | 2026-04-05 |
| 3 | Expand mapping with product-specific 805x accounts | Finance Lead | 2026-04-05 |

## Follow-up Actions — Owner: thijs@powercrumbs.com

| # | Action | Priority |
|---|---|---|
| 1 | Create GL account 8060 "Omzet services" in Exact Online | High |
| 2 | Create GL account 8070 "Omzet abonnementen" in Exact Online | High |
| 3 | Define Zoho Books product categories matching the 805x GL accounts. Current Zoho items use free-text names (e.g., "Hybride A3034"). Thijs must define how these map to categories (biogas, powerbox-20, transport, etc.) and configure them in Zoho. | High |
| 4 | After categories are defined in Zoho, update this mapping table via PR with the exact Zoho category names. | Medium |

## Corrections Applied (from v2.0)

| Original mapping | Issue | Corrected to | Reason |
|---|---|---|---|
| services → 8020 | 8020 is "nultarief" (zero-rate) | services → 8060 (new) | New dedicated account per Finance Lead |
| subscriptions → 8040 | 8040 is "EU reverse charge" | subscriptions → 8070 (new) | New dedicated account per Finance Lead |

## Verification Summary

| Check | Result |
|---|---|
| Mappings with confirmed GL accounts | 10 (default, consulting, products, biogas, wholesale, groengas, powerbox-20, powerbox-10, transport, subsidies-consultancy, overig) |
| Mappings pending GL creation in Exact | 2 (services → 8060, subscriptions → 8070) |
| Mappings pending Zoho category definition | 8 (all 805x product-specific — GL accounts exist but Zoho categories need to be defined) |
| Finance Lead decisions remaining | 0 |

## Validation Rule
- V-03: Every `product_category` on a Zoho Books invoice line must match an entry in this table
- If no match: the "default" account (8000) is used
- If "default" does not exist: validation fails

## Change Process
1. Change request in GitHub
2. Update this table
3. Update automation code if needed
4. Finance Lead approval
