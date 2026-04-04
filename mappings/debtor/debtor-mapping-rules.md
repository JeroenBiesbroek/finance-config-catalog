# Debtor Mapping Rules — Zoho Books Customers to Exact Online Debtors

## Mapping Version
v1.0 — 2026-04-04

## Rules

1. Every Zoho Books customer that generates sales invoices must have a mapped debtor in Exact Online
2. The debtor must be created in Exact Online before the mapping can be added
3. Mapping is by Zoho Books `customer_id` to Exact Online debtor code
4. New mappings require Finance Lead approval

## Mapping Table

| Zoho Books customer_id | Zoho Books customer name | Exact Online debtor code | Exact Online debtor name | Status | Added date |
|---|---|---|---|---|---|
| _example_ | _Example Customer B.V._ | _10001_ | _Example Customer B.V._ | _Active_ | _2026-04-04_ |

> **Note:** Populate this table as customers are onboarded. Each entry requires Finance Lead sign-off.

## Adding a New Debtor Mapping

1. Verify the customer exists in Zoho Books
2. Verify or create the debtor record in Exact Online
3. Add the mapping entry to this table
4. Submit a PR with the updated mapping
5. Finance Lead approves the PR
6. After merge, the sync process will use the new mapping

## Deactivating a Mapping

1. Change status to "Inactive" in this table
2. Document the reason
3. Submit a PR
4. Finance Lead approves
