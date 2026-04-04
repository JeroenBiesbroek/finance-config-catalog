# Account Mapping Rules — Product Categories to GL Accounts

## Mapping Version
v2.0 — 2026-04-05

## Source Extract Date
2026-04-05 (Zoho Books items + Exact Online chart of accounts 8xxx range)

## Rules

1. Each product/service category in Zoho Books maps to a revenue GL account in Exact Online
2. The GL account must exist in the Exact Online chart of accounts
3. A default account is used when no specific category match is found
4. Changes require Finance Lead approval

## Mapping Table

| Product category (Zoho Books) | GL account (Exact Online) | Account description | Status | Verified | Reviewer notes |
|---|---|---|---|---|---|
| default | 8000 | Omzet binnenland hoog tarief | Active | Yes | Confirmed: 8000 exists in Exact. Default fallback for unmapped categories. |
| consulting | 8800 | Omzet honorarium | Active | Yes | Confirmed: 8800 exists. Better match than generic 8010 for consulting. |
| services | 8000 | Omzet binnenland hoog tarief | Active | Pending | Original mapped to 8020 (nultarief) which is incorrect for taxable services. Remapped to 8000. Finance Lead: verify preferred GL. |
| products | 8030 | Netto omzet | Active | Yes | Confirmed: 8030 exists in Exact. |
| subscriptions | 8800 | Omzet honorarium | Active | Pending | Original mapped to 8040 (EU verkoop verlegd) which is a VAT code, not a revenue category. Remapped to 8800. Finance Lead: verify preferred GL. |

## Exact Online Revenue Accounts Available (8xxx)

For reference, these revenue GL accounts exist in the administration:

| GL code | Description | Likely use |
|---|---|---|
| 8000 | Omzet binnenland hoog tarief | Default domestic sales (21%) |
| 8010 | Omzet binnenland laag tarief | Domestic sales (9%) |
| 8020 | Omzet binnenland nultarief | Domestic zero-rate/exempt sales |
| 8030 | Netto omzet | General net revenue |
| 8040 | Verkopen binnen EU verlegd | Intra-EU reverse charge sales |
| 8050 | Omzet biogas premium | Product-specific |
| 8051 | Omzet wholesale | Product-specific |
| 8052 | Omzet groengas | Product-specific |
| 8053 | Verhuur powerbox 20 premium | Product-specific |
| 8054 | Verhuur powerbox 10 premium | Product-specific |
| 8055 | Opbrengst transport premium | Product-specific |
| 8056 | Opbrengst subsidies/consultancy | Product-specific |
| 8057 | Opbrengst overig | Product-specific |
| 8100 | Omzet buitenland intracommunautair | Intra-community sales |
| 8110 | Omzet buitenland buiten EU | Export outside EU |
| 8800 | Omzet honorarium | Consulting/professional services |
| 8900 | Overige bedrijfsopbrengsten | Other operating income |

## Corrections Applied

| Original mapping | Issue | Corrected to | Reason |
|---|---|---|---|
| services → 8020 | 8020 is "nultarief" (zero-rate), not a service revenue category | services → 8000 | Standard domestic high-rate revenue is the correct default for taxable services |
| subscriptions → 8040 | 8040 is "Verkopen binnen EU verlegd" (EU reverse charge), not a subscription category | subscriptions → 8800 | Honorarium/recurring revenue is a closer match; Finance Lead to confirm |

## Decisions Required (Finance Lead)

1. **Services GL account**: Currently mapped to 8000 (domestic high rate default). Should this use a more specific account? Options: 8000, 8030, 8800, or a product-specific 805x.
2. **Subscriptions GL account**: Currently mapped to 8800 (honorarium). Should this use a more specific account? Options: 8800, 8030, or a product-specific 805x.
3. **Product-specific accounts (8050-8057)**: Powercrumbs has detailed product-line revenue accounts (biogas, powerbox, transport, etc.). Should the Zoho Books category mapping be expanded to use these, or should invoices be categorized at this level manually in Exact?

## Validation Rule
- V-03: Every `product_category` on a Zoho Books invoice line must match an entry in this table
- If no match: the "default" account (8000) is used
- If "default" does not exist: validation fails

## Change Process
1. Change request in GitHub
2. Update this table
3. Update automation code if needed
4. Finance Lead approval
