---
name: transport-mode-selection
description: "Use when choosing a transport mode or deciding whether to expedite a late or urgent shipment. Trigger phrases: \"doprava\", \"způsob dopravy\", \"kontejner\", \"paletová přeprava\", \"expres\", \"letecká doprava\", \"air freight\", \"expedite\"."
---

# Skill: Transport Mode Selection

## Purpose

This skill helps the procurement agent choose the most economical transport mode for a shipment, especially when a delivery is late, urgent or non-standard.

The goal is to answer one question: which transport mode meets the required date at the lowest total cost, and is a faster (more expensive) mode worth it compared to the cost of the delay?

It compares sea container (FCL), sea groupage (LCL), rail, full truck (FTL), pallet / groupage road transport (LTL), parcel, express courier and air freight.

## When to use

Use this skill when the user asks about:

- which transport to use (kontejner, paletová, kusová, expres, letecká),
- whether to expedite a late delivery,
- comparing freight offers or modes,
- whether to split a shipment (part by air, rest by sea or truck),
- FCL vs. LCL, FTL vs. pallet transport,
- who pays for expedited transport,
- transport as part of a supply disruption or order consolidation decision.

Typical flow: Supply Disruption Response or Order Consolidation identifies that the date cannot be met with standard transport, then this skill evaluates the transport options.

## Required inputs

If available, collect:

- origin and destination (country, city, pick-up and delivery address type),
- Incoterms (who pays and who organizes transport),
- gross weight (kg),
- volume (cbm) and dimensions,
- number of pallets or packages,
- goods value,
- ready date at the supplier,
- required delivery date (customer or stock-out date),
- customs status (EU or non-EU origin, need for clearance),
- dangerous goods or special handling,
- freight quotes from forwarders, if any,
- cost of delay (see below).

## Transport modes – orientation

Transit times and break-even points below are **orientation values only**. Real values depend on the route, season, carrier and current situation. Always confirm with a forwarder quote.

| Mode | Typical use | Orientation door-to-door time | Notes |
|---|---|---|---|
| Sea FCL (full container) | Large volumes from overseas | Asia → Central Europe approx. 5–7 weeks | Lowest cost per unit for full containers |
| Sea LCL (groupage) | Smaller overseas volumes | Usually longer than FCL due to consolidation | Charged per cbm or tonne, whichever is higher |
| Rail | Asia → Europe alternative | Usually between sea and air | Availability depends on current routes and sanctions |
| Road FTL (full truck) | Large volumes within Europe | approx. 1–4 days within the EU | Dedicated truck, fast and predictable |
| Road LTL / pallet transport | A few pallets within Europe | approx. 2–5 days within the EU | Groupage network, priced per pallet or weight |
| Parcel | Small packages | approx. 1–5 days | Limits on weight and dimensions per package |
| Express courier | Urgent small and medium shipments | approx. 1–3 days within Europe, a few days intercontinental | High cost per kg, door-to-door |
| Air freight | Urgent overseas shipments | approx. 3–7 days door-to-door | High cost; customs and handling at both ends |

## Chargeable weight

Carriers charge the higher of actual weight and volumetric weight. Use the conversion factor from the forwarder quote. Common conventions, to be confirmed:

- Air freight: 1 cbm ≈ 167 kg
- Express courier: 1 cbm ≈ 200 kg
- Road groupage: 1 cbm ≈ 333 kg (or per pallet place)
- Sea LCL: 1 cbm ≈ 1,000 kg (charged per cbm or tonne, whichever is higher)

Chargeable weight = max(actual weight, volume × conversion factor)

## Total transport cost

Compare modes on total cost, not freight only:

Total cost = freight
+ surcharges (fuel, peak season, security)
+ customs clearance and duties (if not already part of the comparison)
+ handling and local charges at both ends
+ insurance
+ inventory carrying cost in transit (goods value × annual rate × days in transit / 365)
+ **cost of delay** (if the mode arrives after the required date)

## Cost of delay

The cost of delay decides whether a faster mode is worth it. Estimate it with the user and sales:

- lost or cancelled customer orders (lost margin, not lost revenue),
- contractual penalties toward the customer,
- cost of a customer's machine standing still (for critical spare parts),
- production or assembly stop,
- extra internal handling and communication,
- relationship risk with a key customer (describe qualitatively if not quantifiable).

## Process

1. Confirm the facts: what ships, from where, when it is ready, by when it must arrive.
2. Calculate chargeable weight for each relevant mode.
3. List feasible modes and their arrival dates (ready date + transit time + customs).
4. Eliminate modes that cannot meet the required date, unless the delay is acceptable.
5. Calculate total cost for each remaining mode.
6. Compare the upgrade cost with the cost of delay:
   upgrade is worth it if (cost of faster mode − cost of standard mode) < cost of delay avoided.
7. Consider a **split shipment**: only the urgent quantity by the fast mode, the rest by the standard mode.
8. Clarify **who pays**: if the delay is caused by the supplier, request that the supplier pays or shares the expedite cost.
9. Recommend one option with reasoning.

## Output format

Use Czech by default.

Return this structure:

1. Shrnutí a doporučení
2. Vstupní údaje a předpoklady
3. Porovnání způsobů dopravy (tabulka: způsob, přepravní čas, termín doručení, celkové náklady, splní termín ano/ne)
4. Výpočet: navýšení nákladů vs. cena zpoždění
5. Varianta rozdělené zásilky (pokud dává smysl)
6. Kdo hradí náklady (Incoterms, odpovědnost dodavatele)
7. Rizika
8. Další kroky (poptávka u speditéra, potvrzení termínu)

## Rules

- Do not invent freight rates. Use quotes provided by the user or clearly mark estimates as orientation values.
- Always state that transit times and conversion factors must be confirmed by the forwarder.
- Compare total cost, not freight only.
- Always include the cost of delay when the decision is about expediting.
- Check Incoterms before assigning transport cost or responsibility.
- For non-EU origin, include customs clearance time and duties.
- Consider sanctions and route restrictions for routes through affected regions.
- Do not book transport or commit on behalf of the company; the recommendation needs human confirmation.
