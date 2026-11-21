# Output Formats

## Output layers (tiers)

The agent serves both experienced buyers and less experienced colleagues. The output is built in up to three layers. The number of layers depends on the task, not on habit: do not overload simple requests.

| Tier | When | Layers delivered |
|---|---|---|
| 1 – Text | quick question, single e-mail (reply, RFQ, counterproposal), clause or document check, short brief | text |
| 2 – Text + Excel | any calculation with two or more variants, or a table with more than ~10 rows: quotation comparison, TCO, spend baseline, allocation of scarce stock, transport cost comparison, rebate or productivity scenarios, scorecard | text + Excel workbook |
| 3 – Text + Excel + visual summary | orange or red supply disruption, management reporting, decision that needs management approval, or the user asks for a dashboard / visual / "pro vedení" | text + Excel workbook + one-page HTML visual summary |

Rules:

1. Decide the tier at the start and state it in one line, e.g. "Úroveň výstupu: 3 (text + Excel + vizuální souhrn)".
2. The user can always override: "jen text", "přidej Excel", "udělej i dashboard".
3. End every tier 1 or tier 2 output with a one-line offer of the next layer, e.g. "Mám k tomu připravit Excel s výpočtem?" Do not offer anything on tier 3.
4. If the environment cannot create files (e.g. no file tools), deliver the Excel layer as a clearly structured table in the text and say so in one line.

### Layer 1 – Text (always)

Every output longer than a few paragraphs starts with this block. Short answers and single e-mail drafts skip it.

```markdown
## Na 30 sekund
- **Verdikt:** jedna věta – co se děje a co doporučuji.
- **Udělej dnes:** 1. … 2. … 3. … (max. 3 kroky, každý s odpovědností / termínem, pokud je znám)
- **Klíčové číslo:** jedno číslo, které rozhoduje (dopad, úspora, náklad řešení).
- **Hlavní riziko:** jedna věta.
- **Kdo rozhoduje / schvaluje:** role (nákup, kvalita, obchod, vedení).
```

The detailed analysis follows below the block in the structure of the applied skill. A less experienced user must be able to act correctly after reading only this block.

### Layer 2 – Excel workbook (single source of numbers)

When the Excel layer is produced, build it FIRST and take every number in the text and in the visual summary from it. Never calculate the same figure twice in different places.

Workbook structure (Czech sheet names):

| Sheet | Content |
|---|---|
| Souhrn | the "Na 30 sekund" block, key numbers linked by formulas to the calculation sheets |
| Vstupy | all input data as received (prices, quantities, dates, terms), source of each value |
| Výpočty | calculations with live formulas, no hard-coded results |
| Varianty | side-by-side comparison of options (cost, timing, risk) |
| Předpoklady | numbered assumptions (P1, P2, …) with impact if wrong |
| Akce | action list: krok, odpovědnost, termín, stav |

Rules:

- Inputs in one colour (blue font), formulas in black; mark assumptions clearly.
- Formulas must recalculate when an input changes, so the user can test scenarios.
- File name: `<téma>_<YYYY-MM-DD>.xlsx`, e.g. `NK-220_zpozdeni_2026-11-23.xlsx`.
- Omit sheets that would stay empty (e.g. no Akce sheet for a pure price comparison).

### Layer 3 – Visual summary (one-page HTML)

A one-page, self-contained HTML file for fast understanding (management, sales, colleagues). Use the **Decision summary** mode of the Excel Procurement Dashboard skill and its template `decision_summary_template.html`.

It shows only: the "Na 30 sekund" block, 3–6 KPI cards, variant comparison, timeline of key dates, action list and top risks. No new numbers – everything comes from the Excel layer.

### Consistency check (tier 2 and 3)

Before delivering, verify that the key numbers (total impact, cost of recommended option, key quantities and dates) are identical in the text, the workbook and the visual summary. If not, fix them before delivery.


## Default procurement output

Use this structure unless a skill defines a more specific one:

```markdown
## 1. Shrnutí
Krátké manažerské shrnutí.

## 2. Vstupní data
Co bylo poskytnuto a z čeho analýza vychází.

## 3. Zjištění
Fakta z dokumentů, cen, nabídek nebo zadání.

## 4. Výpočet / porovnání
Tabulka, scénář nebo srovnání.

## 5. Rizika a nejasnosti
Co může ovlivnit rozhodnutí.

## 6. Doporučení
Jasný návrh dalšího postupu.

## 7. Další kroky
Konkrétní akce pro nákupčího.
```

## Supplier comparison table

```markdown
| Dodavatel | Cena | Měna | Jednotka | Incoterms | Lead time | Platební podmínky | Rizika | Poznámka |
|---|---:|---|---|---|---|---|---|---|
```

## Management summary

```markdown
## Executive summary
- Main message:
- Financial impact:
- Key risks:
- Recommended decision:
- Required management action:
```

## Negotiation brief

```markdown
## Vyjednávací brief
### Cíl
### Výchozí pozice
### Argumenty
### Ústupky
### BATNA
### Doporučený postup
### Návrh e-mailu / talking points
```

## RFQ email

```markdown
Předmět: RFQ – [kategorie / položka] – [termín odpovědi]

Dobrý den,

prosíme o cenovou nabídku na níže uvedené položky:

[tabulka položek]

Prosíme o uvedení:
- ceny a měny,
- jednotky,
- Incoterms,
- dodací lhůty,
- platebních podmínek,
- MOQ,
- platnosti nabídky,
- technických odchylek,
- případných dodatečných nákladů.

Termín pro zaslání nabídky: [datum]

Děkuji a přeji hezký den.
```
