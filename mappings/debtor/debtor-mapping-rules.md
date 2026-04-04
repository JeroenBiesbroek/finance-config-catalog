# Debtor Mapping Rules — Zoho Books Customers to Exact Online Debtors

## Mapping Version
v2.1 — 2026-04-04

## Source Extract Date
2026-04-04

## Rules

1. Every Zoho Books customer that generates sales invoices must have a mapped debtor in Exact Online
2. The debtor must be created in Exact Online before the mapping can be added
3. Mapping is by Zoho Books `customer_id` to Exact Online debtor code
4. New mappings require Finance Lead approval

## Mapping Table — Matched (24 customers)

| Zoho Books customer_id | Zoho Books customer name | Exact Online debtor code | Exact Online debtor name | Status | Reviewer notes | Added date |
|---|---|---|---|---|---|---|
| 716964000001662133 | Kisjes Transport B.V. | 418 | Kisjes Transport B.V. | Active | Exact match | 2026-04-04 |
| 716964000001608361 | Hanab Energy Solutions B.V. | 417 | Hanab Energy Solutions B.V. | Active | Duplicate in Exact (404 and 417). Using 417 — verify which is active. | 2026-04-04 |
| 716964000001528761 | Koninklijke Van Twist B.V. | 424 | Koninklijke Van Twist B.V. | Active | Duplicate in Exact (222 and 424). Using 424 — verify which is active. | 2026-04-04 |
| 716964000001528745 | Genpower B.V. | 421 | Genpower B.V. | Active | Exact match | 2026-04-04 |
| 716964000001528641 | Bredenoord B.V. | 419 | Bredenoord B.V. | Active | Duplicate in Exact (164 and 419). Using 419 — verify which is active. | 2026-04-04 |
| 716964000000936003 | KWS Infra B.V. | 172 | KWS Infra BV Amsterdam-Utrecht | Active | Name differs slightly. Zoho: "KWS Infra B.V.", Exact: "KWS Infra BV Amsterdam-Utrecht". Confirm same entity. | 2026-04-04 |
| 716964000000882145 | Martens en Van Oord Aannemingsbedrijf B.V. | 393 | Martens en Van Oord Aannemingsbedrijf B.V. | Active | Exact match | 2026-04-04 |
| 716964000000883101 | VolkerWessels Materieel & Logistiek B.V. | 226 | VolkerWessels Materieel & Logistiek | Active | Minor name difference (B.V. suffix). Same entity. | 2026-04-04 |
| 716964000000714065 | Heijmans Infra B.V. | 86 | Heijmans Infra B.V. | Active | Exact match | 2026-04-04 |
| 716964000000679061 | Heijmans Materieel Beheer B.V. | 420 | Heijmans Materieel Beheer B.V. | Active | Exact match | 2026-04-04 |
| 716964000000675106 | BAM Energie & Water B.V. | 415 | BAM Energie & Water B.V. | Active | Exact match | 2026-04-04 |
| 716964000000680003 | Gebr. Van der Poel B.V. | 413 | Gebr. van der Poel B.V. | Active | Case difference only ("Van" vs "van"). Same entity. | 2026-04-04 |
| 716964000000521028 | Van den Biggelaar Grond- en waterbouw B.V. | 296 | Van den Biggelaar Grond- en waterbouw B.V. | Active | Exact match | 2026-04-04 |
| 716964000000244597 | AsfaltNu C.V. | 410 | AsfaltNu C.V. | Active | Exact match | 2026-04-04 |
| 716964000000238001 | Powercrumbs | 333 | Powercrumbs BV | Active | Minor name difference ("Powercrumbs" vs "Powercrumbs BV"). Own company. | 2026-04-04 |
| 716964000000208003 | Sterk B.V. | 414 | Sterk B.V. | Active | Exact match | 2026-04-04 |
| 716964000000106068 | Kabelwerken van Dorp B.V. | 334 | Kabelwerken van Dorp B.V. | Active | Exact match | 2026-04-04 |
| 716964000000100081 | Dijkzone Alliantie Zwolle v.o.f. | 324 | Dijkzone Alliante Zwolle VOF | Active | Spelling difference ("Alliantie" vs "Alliante", "v.o.f." vs "VOF"). Confirm same entity. | 2026-04-04 |
| 716964000000064273 | Boskalis Nederland B.V. | 416 | Boskalis Nederland B.V. | Active | Exact match | 2026-04-04 |
| 716964000000064213 | Combinatie Maasamen | 284 | Combinatie Maasamen | Active | Exact match | 2026-04-04 |
| 716964000000064197 | Combinatie Dijkalliantie Neder-Betuwe v.o.f. | 412 | Combinatie Dijkalliantie Neder-Betuwe v.o.f. | Active | Exact match | 2026-04-04 |
| 716964000000064181 | Koop Bronbemaling B.V. | 245 | Koop Bronbemaling B.V. | Active | Exact match | 2026-04-04 |
| 716964000000064149 | GMB Civiel B.V. | 411 | GMB Civiel B.V. | Active | Exact match | 2026-04-04 |
| 716964000000064133 | Van Gelder Groep B.V. | 244 | Van Gelder KLM | Active | Finance Lead confirmed: Van Gelder Groep B.V. = Van Gelder KLM. Approved 2026-04-04. | 2026-04-04 |

## Unmatched Customers (4 customers) — Action owner: thijs@powercrumbs.com

These customers need investigation and resolution in Exact Online before they can be mapped. Finance Lead has assigned this to Thijs.

| Zoho Books customer_id | Zoho Books customer name | Zoho receivable | Unmatched reason | Required action |
|---|---|---|---|---|
| 716964000002209003 | Bouwhuis Aannemingsmaatschappij "Bouwmij" B.V. | €0,00 | No debtor found in Exact Online | Thijs: create debtor in Exact, then add mapping via PR |
| 716964000001962086 | AsfaltNu Amsterdam I | €86.394,00 | No exact match. AsfaltNu C.V. (410) exists but is mapped to separate Zoho entity. | Thijs: decide if this maps to 410 or needs new debtor. HIGH PRIORITY — has €86K receivable. |
| 716964000001327555 | Critical Energy Services Europe B.V. | €0,00 | No debtor found in Exact Online | Thijs: create debtor in Exact, then add mapping via PR. Low urgency. |
| 716964000000678065 | Renewable Energy Drilling B.V. | €0,00 | No debtor found in Exact Online | Thijs: create debtor in Exact, then add mapping via PR. Low urgency. |

## Excluded Customers (1)

| Zoho Books customer_id | Zoho Books customer name | Reason |
|---|---|---|
| 716964000000381003 | Test Klant Facturering | Test account. Not mapped. Consider deactivating in Zoho Books. |

## Duplicate Debtor Codes in Exact Online — Action owner: thijs@powercrumbs.com

The following Exact Online debtor names appear under multiple codes. The mapping currently uses the higher code (most recently created). Thijs must verify which code is the active debtor account, confirm or update the mapping, and deactivate the unused code in Exact.

| Exact debtor name | Code used in mapping | Duplicate code | Action needed |
|---|---|---|---|
| Hanab Energy Solutions B.V. | 417 | 404 | Thijs: verify active code, deactivate duplicate, confirm mapping |
| Koninklijke Van Twist B.V. | 424 | 222 | Thijs: verify active code, deactivate duplicate, confirm mapping |
| Bredenoord B.V. | 419 | 164 | Thijs: verify active code, deactivate duplicate, confirm mapping |

## Validation Summary

| Check | Result |
|---|---|
| Total Zoho Books active customers | 29 |
| Matched to Exact debtor | 24 |
| Needs review | 0 |
| Unmatched (pending Thijs) | 4 |
| Excluded (test account) | 1 |
| Duplicate Zoho customer_id entries | 0 |
| Duplicate Exact debtor code entries in mapping | 0 |
| Duplicate debtor names in Exact (pending Thijs) | 3 |
| Records requiring Finance Lead decision | 0 |
| Records requiring Thijs action | 7 (4 unmatched + 3 duplicate verifications) |

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
