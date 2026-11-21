---
name: supplier-rebate
description: "Use when designing, negotiating, calculating or tracking a supplier volume or turnover rebate. Trigger phrases: \"obratový bonus\", \"odběrový bonus\", \"volume rebate\", \"rebate\", \"bonus za odběr\", \"bonusová pásma\", \"vyúčtování bonusu\"."
---

# Skill: Supplier Rebate

## Purpose

This skill helps the procurement agent design, negotiate, calculate and track volume or turnover rebates with suppliers.

The goal is a rebate structure that is clear, measurable and actually paid, and a sound comparison of a rebate against a direct price discount.

## When to use

Use this skill when the user asks about:

- volume or turnover rebate (obratový / odběrový bonus),
- rebate tiers and thresholds,
- rebate vs. price discount decision,
- rebate clause for a contract amendment,
- rebate settlement and claim,
- tracking of turnover against rebate thresholds.

## Required inputs

If available, collect:

- supplier name,
- turnover with the supplier (last 12 months and forecast),
- product scope,
- existing rebate or discount agreements,
- supplier proposal (if any),
- payment terms,
- contract and accounting constraints,
- year-to-date turnover (for tracking).

## Rebate design elements

Define each element explicitly:

| Element | Options |
|---|---|
| Base | net turnover excluding VAT, after returns and credit notes |
| Period | calendar year, fiscal year, quarter |
| Scope | all products or selected groups |
| Tiers | thresholds and percentages |
| Calculation type | retroactive from the first crown once a threshold is reached, or incremental only on turnover above the threshold |
| Growth component | optional extra % for growth vs. previous year |
| Settlement | credit note, payment, or deduction from invoices |
| Timing | quarterly or annual settlement, deadline for supplier |
| Conditions | payment discipline, exclusions, what happens if the threshold is not reached |

## Process

1. Understand current turnover, forecast and the supplier's position.
2. Propose a rebate structure with tiers that are ambitious but reachable.
3. Calculate scenarios: low, expected and high turnover.
4. Compare the rebate with a direct price discount.
5. Prepare the contract clause points for an amendment.
6. Draft the supplier email or proposal.
7. Set up tracking: year-to-date turnover vs. thresholds, forecast to period end, reminders before settlement.
8. At period end, prepare the rebate claim.

## Calculation

- Retroactive: rebate = total period turnover × % of the highest tier reached
- Incremental: rebate = Σ (turnover within each tier × that tier's %)
- Expected value = rebate × probability of reaching the tier
- Show all scenarios in a table.

## Rebate vs. price discount

A rebate is not the same as a discount:

- a discount is certain and lowers the price immediately,
- a rebate is paid later and only if the volume is reached,
- a rebate does not lower the visible unit price, so sales see a higher purchase price unless net-net prices are shared.

As a rule, a rebate of r % is worth roughly the same as a discount of d % only if r × probability of reaching the threshold ≥ d, adjusted for later payment. Recommend a discount when volume is uncertain, and a rebate when it stimulates growth or consolidation.

## Output format

Use Czech by default unless supplier communication should be in English.

Return this structure:

1. Shrnutí
2. Doporučená struktura bonusu (tabulka pásem)
3. Výpočet a scénáře
4. Srovnání bonus vs. sleva
5. Body do smluvního dodatku
6. Návrh e-mailu / návrhu dodavateli
7. Sledování plnění
8. Rizika

## Rules

- Never count the same money twice: a rebate is not also a price saving.
- Final contract wording must be confirmed by legal.
- Accounting treatment (accruals during the year) must be confirmed with finance.
- Define every term unambiguously: base, period, scope, calculation type and settlement.
- Do not promise volumes the company cannot commit to.
- Keep supplier communication professional.
