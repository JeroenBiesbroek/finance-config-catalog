# Debtor Mapping Rules — Zoho Books Customers to Exact Online Debtors

## Mapping Version
v1.0 — 2026-04-04

## Rules

1. Every Zoho Books customer that generates sales invoices must have a mapped debtor in Exact Online
2. The debtor must be created in Exact Online before the mapping can be added
3. Mapping is by Zoho Books `customer_id` to Exact Online debtor code
4. New mappings require Finance Lead approval

## Mapping Table

<!-- CFG-004: Replace the entries below with actual Zoho Books customer_id and Exact Online debtor codes.
     Instructions:
     1. Export active customers from Zoho Books (Settings > Contacts > Export)
     2. Export debtors from Exact Online (CRM > Accounts > Export)
     3. Match by customer name
     4. Fill in each row
     5. Remove this comment block when done -->

| Zoho Books customer_id | Zoho Books customer name | Exact Online debtor code | Exact Online debtor name | Status | Added date |
|---|---|---|---|---|---|
| <!-- REPLACE --> | <!-- REPLACE --> | <!-- REPLACE --> | <!-- REPLACE --> | Active | 2026-04-04 |

> **Action required:** Replace the placeholder row(s) above with actual customer-to-debtor mappings from your Zoho Books and Exact Online administrations. Each entry requires Finance Lead sign-off.

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
