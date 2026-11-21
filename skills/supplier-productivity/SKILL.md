---
name: supplier-productivity
description: "Use when preparing an annual productivity or cost-reduction request to suppliers. Trigger phrases: \"produktivita\", \"požadavek na produktivitu\", \"roční snížení cen\", \"cost reduction\", \"productivity request\", \"annual price review\", \"úspory u dodavatelů\"."
---

# Skill: Supplier Productivity

## Purpose

This skill helps the procurement agent prepare and run an annual productivity request to suppliers: a structured demand for year-on-year cost reduction, backed by facts and paired with ideas for how the supplier can reach it.

The goal is a realistic, well-argued target for each selected supplier, a clear request letter, a negotiation plan and a way to track realized savings.

## When to use

Use this skill when the user asks about:

- annual productivity request,
- year-on-year price reduction,
- cost-down program,
- annual price review with suppliers,
- savings target per supplier,
- productivity letter or email,
- tracking of realized productivity.

## Required inputs

If available, collect:

- spend per supplier (last 12 months),
- price history of key items,
- forecast volumes for the next period,
- relevant market indices (raw materials, energy, labour, FX),
- benchmarks or competing offers,
- contract status and price clauses,
- supplier dependency (single source, switching cost),
- supplier performance (OTIF, quality),
- company savings target.

## Process

1. **Select suppliers.** Focus on the top spend and on suppliers where leverage exists. Segment them (for example by spend and supply risk) and decide the approach per segment.
2. **Set a target per supplier** with clear reasoning, typically in the range of a few percent. Do not apply one flat number to everyone.
3. **Build the argument**: volume and growth, index development, benchmark gaps, supplier learning curve, payment discipline, relationship length.
4. **Choose the levers** beyond a pure price cut:
   - price reduction on selected items,
   - value analysis / value engineering (specification, material, tolerances),
   - packaging and logistics changes,
   - consolidation of volumes,
   - longer contract or volume commitment in exchange for price,
   - payment terms,
   - consignment or VMI.
5. **Calculate the impact**: annualized saving and in-year saving depending on the effective date.
6. **Prepare the request** letter or email per supplier.
7. **Plan the negotiation**: target, minimum acceptable result, give-gets, fallback.
8. **Track realization**: agreed vs. realized savings, by month.

## Calculation

- Annualized saving = Σ (old price − new price) × forecast annual volume
- In-year saving = annualized saving × (remaining months after effective date / 12)
- Distinguish **price reduction** (real saving against current price) from **cost avoidance** (rejected price increase). Report them separately.

## Output format

Use Czech by default unless supplier communication should be in English.

Return this structure:

1. Shrnutí
2. Výběr dodavatelů a cíle (tabulka: dodavatel, spend, cíl %, cíl v Kč, odůvodnění)
3. Argumenty pro vyjednávání
4. Páky mimo čistou cenu
5. Výpočet dopadu (roční a v aktuálním roce)
6. Návrh dopisu / e-mailu dodavateli
7. Plán vyjednávání a fallback
8. Sledování plnění

## Rules

- Do not invent benchmarks, indices or competing offers. Mark estimates as estimates.
- Do not apply aggressive targets to critical single-source suppliers without assessing supply risk.
- Separate price reduction from cost avoidance in all reporting.
- Check contract price clauses before requesting changes.
- Keep supplier communication professional and partnership-oriented; productivity is a joint effort, not a threat.
- Do not reveal internal targets unless the user explicitly asks.
