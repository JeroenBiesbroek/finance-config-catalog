# Account Mapping Rules — Product Categories to GL Accounts

## Mapping Version
v1.0 — 2026-04-04

## Rules

1. Each product/service category in Zoho Books maps to a revenue GL account in Exact Online
2. The GL account must exist in the Exact Online chart of accounts
3. A default account is used when no specific category match is found
4. Changes require Finance Lead approval

## Mapping Table

| Product category (Zoho Books) | GL account (Exact Online) | Account description | Status |
|---|---|---|---|
| default | 8000 | Omzet overig | Active |
| consulting | 8010 | Omzet consultancy | Active |
| services | 8020 | Omzet dienstverlening | Active |
| products | 8030 | Omzet producten | Active |
| subscriptions | 8040 | Omzet abonnementen | Active |

> **Note:** Add categories as your product/service offering expands. The "default" entry is the fallback.

## Validation Rule
- V-03: Every `product_category` on a Zoho Books invoice line must match an entry in this table
- If no match: the "default" account is used
- If "default" does not exist: validation fails

## Change Process
1. Change request in GitHub
2. Update this table
3. Update automation code if needed
4. Finance Lead approval
