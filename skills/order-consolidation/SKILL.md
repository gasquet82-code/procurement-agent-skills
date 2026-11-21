---
name: order-consolidation
description: "Use when customer orders wait for parts from several suppliers and need prioritization, partial vs. complete shipment decisions or stock allocation. Trigger phrases: \"kompletace zakázek\", \"zákazník čeká na kompletní dodávku\", \"chybějící položky\", \"částečná expedice\", \"backlog\"."
---

# Skill: Order Consolidation

## Purpose

This skill helps the procurement agent manage customer orders that contain parts from several suppliers and can only be shipped once they are complete, or when a partial shipment is agreed.

The goal is to:

- see which lines block each customer order,
- decide which orders get priority and why,
- decide whether to wait for the complete order or ship partially,
- allocate scarce stock between competing orders,
- focus purchasing actions on the lines that really block shipments,
- communicate a realistic completion date to sales and customers.

## When to use

Use this skill when the user asks about:

- kompletace zakázek / objednávek,
- customer waiting for a complete delivery,
- order backlog with missing lines,
- which order to complete first,
- partial vs. complete shipment,
- allocation of scarce stock between customers,
- open order report with missing parts.

Typical flow: Excel Procurement Analysis reads the open order list, this skill prioritizes the orders and bottleneck lines, then Supply Disruption Response and Transport Mode Selection are used for the critical blocking lines.

## Required inputs

If available, collect for each customer order:

- customer and customer segment (A / B / C, strategic, dealer, end user),
- country and shipping method (domestic, export, container, pallet),
- order lines: part number, quantity, value, margin,
- status of each line (see below),
- ETA of each line not in stock,
- customer due date and promised date,
- contractual penalties or special conditions,
- customer preference: complete delivery only, or partial deliveries accepted,
- urgency signal: machine standing still / vehicle off road (VOR),
- order age (days since order),
- shipping cost of an additional partial shipment.

## Line status

Classify each order line:

| Status | Meaning |
|---|---|
| In stock | Available and can be allocated |
| In transit | Shipped by supplier, ETA known |
| Ordered – confirmed | Purchase order confirmed with a date |
| Ordered – unconfirmed | Purchase order sent, no confirmed date |
| Not ordered | Missing line without a purchase order (action needed immediately) |

**Completion date of an order = latest confirmed ETA of its lines.** Unconfirmed or not ordered lines mean the completion date is unknown.

## Prioritization

Score each order on these criteria. The weights are a starting point and should be agreed with sales.

| Criterion | Why it matters | Example scoring |
|---|---|---|
| Urgency (machine down / VOR) | A standing machine costs the customer money every day | Yes = highest priority regardless of other criteria |
| Customer importance | Strategic customers drive future business | A = 3, B = 2, C = 1 |
| Due date and penalties | Missed dates damage trust and may cost money | Overdue or penalty = 3 |
| Order value and margin | More money at stake | Top 20 % of open value = 3 |
| Completion level | Orders close to complete are cheap to finish | ≥ 80 % lines available = 3 |
| Order age | Old orders frustrate customers | Over X days = 2 |
| Shipping economics | Export shipments are expensive to split | Container / overseas = prefer complete |

Output a ranked list with the reason for each order's priority.

## Partial vs. complete shipment

Recommend per order:

- **Ship partially now** when: the customer has a machine down, the customer accepts partial deliveries and the extra freight is small, or the missing lines have no confirmed date.
- **Wait and ship complete** when: the missing lines arrive soon with a confirmed date, the shipment is export or container-based where a second shipment is expensive, or the customer requires complete deliveries.
- **Escalate** when: a high-priority order is blocked by an unconfirmed or not ordered line.

Always state the extra cost of a partial shipment and the expected waiting time for a complete one.

## Allocation of scarce stock

When one part is needed by several orders:

1. Allocate by priority rank, not by order date alone.
2. Do not take stock from an order that would otherwise ship complete, unless the receiving order has a higher urgency (machine down).
3. Show the effect of each allocation: which orders become complete and which wait.

## Purchasing actions on bottleneck lines

For lines that block high-priority orders:

- request confirmation or an earlier date from the supplier,
- use Supply Disruption Response if the supplier is late,
- use Transport Mode Selection to check whether expediting pays off,
- consider a substitute part or an alternative supplier or distributor,
- group lines by supplier so one escalation covers several orders.

## Prevention

Recommend process improvements:

- check availability of all lines when the customer order is entered,
- order missing lines immediately, not when the rest is ready,
- set a target completion date per order and track it,
- regular backlog review with sales (for example weekly),
- safety stock for parts that often block orders,
- KPIs: share of orders shipped complete and on time, average days waiting for the last line, number of partial shipments and their extra freight cost, backlog value and age.

## Output format

Use Czech by default.

Return this structure:

1. Shrnutí
2. Přehled otevřených zakázek a blokujících položek
3. Pořadí priorit s odůvodněním
4. Doporučení pro každou prioritní zakázku: částečná expedice / čekat na kompletaci / eskalovat
5. Rozdělení nedostatkového zboží (pokud je potřeba)
6. Akce nákupu na blokujících položkách (seskupené podle dodavatele)
7. Informace pro obchod a zákazníky (realistické termíny)
8. Prevence a KPI

## Rules

- Never promise a completion date that depends on unconfirmed supplier dates. State the uncertainty.
- Make priority criteria transparent and agree the weights with sales; do not decide customer priority alone.
- Do not reallocate stock from a complete order without explaining the impact.
- Separate confirmed ETAs from estimates.
- Customer communication goes through sales unless the user says otherwise.
- Do not make binding commitments to customers or suppliers on behalf of the company.
