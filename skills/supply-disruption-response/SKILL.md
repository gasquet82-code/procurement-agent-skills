---
name: supply-disruption-response
description: "Use when a supplier delivery is delayed or supply is disrupted and customers or production are at risk. Trigger phrases: \"zpoždění dodávky\", \"dodavatel nestíhá\", \"zákazník čeká\", \"narušení dodávek\", \"supply disruption\", \"delivery delay\", \"expedite\"."
---

# Skill: Supply Disruption Response

## Purpose

This skill helps the procurement agent manage a supply disruption from the first signal to prevention.

The goal is to protect the customer and the business: understand the real impact, choose the best recovery option, communicate truthfully to all sides and prevent the same disruption from happening again.

It goes beyond reading a delay email. It produces a recovery plan.

## When to use

Use this skill when:

- a supplier announces or causes a delivery delay,
- a supplier delivers only partially,
- a delivery is blocked for quality reasons,
- a supplier lacks capacity or allocates volumes,
- force majeure is claimed,
- logistics, customs, sanctions or compliance block a delivery,
- there are signs of supplier financial distress,
- a customer order or production is at risk because of missing parts.

Typical flow: Email Procurement Analysis extracts the facts from the supplier email, then this skill takes over when customer or business impact is identified.

## Required inputs

If available, collect:

- supplier name and contact,
- affected items (part numbers, quantities),
- original confirmed delivery date,
- new date and whether it is confirmed in writing,
- reason stated by the supplier,
- open purchase orders,
- current stock and stock in transit,
- affected customer orders, customers and their due dates,
- customer importance and contractual penalties toward customers,
- contract with the supplier (delivery terms, penalties, force majeure clause),
- alternative suppliers, distributors or substitute parts,
- supplier history (OTIF, previous delays).

## Disruption types

Identify the type, because it changes the options:

- Delay of a confirmed delivery
- Partial delivery
- Quality block (delivered goods not usable)
- Capacity shortfall or allocation
- Force majeure claim
- Logistics or customs problem
- Sanctions or compliance block
- Supplier financial distress or insolvency risk

## Severity levels

Classify the disruption and set the escalation accordingly.

| Level | Meaning | Who must be informed |
|---|---|---|
| Green | No customer impact, stock or buffer covers the gap | Buyer |
| Orange | A customer order is at risk or will be partially late | Buyer, category owner, sales |
| Red | Key customer, large order or penalty at stake, or no stock and no quick alternative | Head of purchasing, sales director, management; daily status until resolved |

## Process

1. **Stabilize the facts.** What exactly is late, by how much, what the supplier confirmed in writing and what is only a promise. Build a short timeline.
2. **Assess the impact.** Which customer orders and customers are affected, value at risk (sales, margin, penalties), relationship risk, stock coverage in days.
3. **Classify** the disruption type and severity level.
4. **Generate options** and evaluate each by cost, speed, risk and who pays.
5. **Recommend** one option or a combination, with reasoning.
6. **Prepare communication** for the supplier, internal sales or customer, and management.
7. **Define prevention**: root cause, scorecard entry, contractual remedies, second source, safety stock review.

## Recovery options

Evaluate where relevant:

- Expedite: express or air freight, overtime at supplier. Clarify who pays and request supplier cost participation when the delay is the supplier's fault.
- Partial or split deliveries: prioritize the lines needed by the most critical customer orders.
- Reallocation: use own stock or stock reserved for less urgent orders.
- Substitute part: equivalent part or cross-reference. Requires technical and quality approval.
- Spot buy: alternative supplier or distributor, even at a higher price, when the margin or relationship at stake justifies it.
- Customer side: split delivery, revised date or substitute agreed with the customer through sales.
- Temporary safety stock increase for the affected items until the supplier recovers.

Present options as a table:

| Option | Cost | Speed | Risk | Who pays | Recommendation |
|---|---|---|---|---|---|

## Communication

Prepare drafts for:

1. **Supplier escalation email**: facts, impact, required recovery date, required written confirmation, request for recovery plan, cost participation, response deadline. Standard tone by default, firm tone for repeated failures.
2. **Internal update for sales**: what is late, realistic date with buffer, options for the customer, what sales may and may not promise.
3. **Management brief** (Orange and Red only): 5 lines maximum: situation, impact, chosen action, cost, next update.

## Prevention

After the disruption is stabilized, recommend:

- root cause analysis (8D for quality issues),
- entry into the supplier scorecard (OTIF, incident),
- contractual remedies: penalties, liquidated damages, check of force majeure validity,
- second source evaluation for critical single-source items,
- safety stock and reorder point review,
- supplier recovery plan with milestones and follow-up meeting.

## Output format

Use Czech by default.

Output tier: yellow = tier 1 or 2, orange and red = tier 3 (text + Excel + visual summary), see `global/OUTPUT_FORMATS.md`.

Return this structure:

0. Na 30 sekund
1. Shrnutí situace
2. Typ narušení a úroveň závažnosti
3. Fakta vs. předpoklady (časová osa)
4. Dopad na zákazníky a byznys
5. Možnosti řešení (tabulka)
6. Doporučené řešení
7. Návrh e-mailu dodavateli
8. Interní informace pro obchod
9. Shrnutí pro vedení (jen u oranžové a červené)
10. Prevence a další kroky

## Rules

- Never promise a customer date that the supplier has not confirmed in writing. Add a realistic buffer.
- Always separate confirmed facts from assumptions and supplier promises.
- Check the contract before threatening penalties or claiming damages.
- If force majeure is claimed, ask for evidence and state that legal should confirm validity.
- Substitute parts require technical and quality approval before use.
- Keep supplier communication professional and factual, without blame language.
- Do not make binding commitments on behalf of the buyer or the company.
- Document the timeline of events for later claims and supplier evaluation.
- Check every key date against the calendar: weekends and public holidays at the supplier, the carrier and our site. Flag dates that fall on a weekend and plan inspection and dispatch on working days.
- Customer communication about an alternative or unapproved source goes out only after (1) quality release and (2) a check that the customer contract allows a change of source without approval. Until then, inform the customer about the plan and the date, not the source.
- Keep messages consistent: the internal summary, the supplier e-mail and the customer e-mail must state the same position (e.g. "price increase not accepted in this form, under negotiation" – not "rejected" in one place and "open to indexation" in another).
