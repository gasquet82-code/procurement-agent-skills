---
name: procurement-task-router
description: Use this skill when the user's request involves procurement task router. Trigger phrases include: "procurement task", "task router", "jaký skill použít", "použij správné skilly", "kombinuj skilly", "orchestration", "routing", "analyzuj zadání", "vyber skill", "komplexní procurement úkol", "procurement workflow", "procurement copilot".
---

# Skill: Procurement Task Router

## Purpose

This skill helps the procurement agent identify the type of procurement task, select the most relevant primary skill, select supporting skills and define the correct output structure.

The goal is to make the procurement agent behave as an orchestrated procurement system, not as a collection of isolated skills.

This skill should be used at the beginning of complex or unclear procurement tasks.

## When to use

Use this skill when:

- the user request is broad, mixed or unclear,
- the task may require multiple skills,
- the user uploads files or provides data without specifying the exact output,
- the user asks for analysis, recommendation, strategy or management output,
- the user asks to compare, review, negotiate, summarize or prepare a response,
- the agent needs to decide which procurement methodology to apply.

## Core routing logic

Always identify:

1. What is the input?
2. What is the procurement task?
3. What decision or output does the user need?
4. What is the primary skill?
5. What supporting skills are needed?
6. What data is missing?
7. What output format is appropriate?

## Input type routing

### Excel / spreadsheet input

Primary skill:

- Excel Procurement Analysis

Supporting skills depending on content:

- Supplier Quotation Comparison
- TCO Analysis
- Spend Baseline Analysis
- Supplier Scorecard
- Management Procurement Reporting

Use when the input contains:

- RFQ matrix,
- price list,
- spend data,
- supplier list,
- TCO model,
- supplier scorecard data,
- order / invoice data.

### Email input

Primary skill:

- Email Procurement Analysis

Supporting skills depending on content:

- Supplier Counterproposal
- Contract Commercial Review
- Supplier Quotation Comparison
- Negotiation Brief
- Supply Disruption Response
- Supplier Productivity
- Supplier Rebate

Use when the input contains:

- supplier offer,
- RFQ response,
- delivery confirmation,
- price increase notice,
- complaint,
- negotiation message,
- supplier escalation.

If the email reports a delay, partial delivery, quality block or other supply disruption that puts customer orders or stock at risk, hand over to Supply Disruption Response after extracting the facts.

### Word / PDF / document input

Primary skill:

- Document Review Word PDF

Supporting skills depending on content:

- Contract Commercial Review
- Supplier Counterproposal
- SDS / compliance-related review if available
- Supplier Quotation Comparison
- Management Procurement Reporting

Use when the input contains:

- supplier offer,
- contract draft,
- commercial terms,
- technical specification,
- datasheet,
- certificate,
- SDS,
- REACH declaration,
- supplier presentation.

### Supplier offer / quotation

Primary skill:

- Supplier Quotation Comparison

Supporting skills:

- TCO Analysis
- Contract Commercial Review
- Supplier Counterproposal
- Management Procurement Reporting

Use when the user asks to:

- compare offers,
- recommend supplier,
- identify best offer,
- prepare negotiation arguments,
- explain why cheapest price may not be best.

### Contract / commercial terms

Primary skill:

- Contract Commercial Review

Supporting skills:

- Supplier Counterproposal
- Negotiation Brief
- Management Procurement Reporting

Use when the task contains:

- payment terms,
- Incoterms,
- MOQ,
- SLA,
- warranty,
- liability,
- termination,
- price validity,
- price indexation,
- contract red flags.

### Supplier response / counterproposal

Primary skill:

- Supplier Counterproposal

Supporting skills:

- Negotiation Brief
- Contract Commercial Review
- Supplier Quotation Comparison

Use when the user asks to:

- reply to supplier,
- prepare counteroffer,
- request revised terms,
- write negotiation email,
- respond to offer,
- push back on commercial terms.

### Category strategy / management topic

Primary skill:

- Procurement Category Strategy

Supporting skills:

- Spend Baseline Analysis
- Supplier Portfolio Review
- Management Procurement Reporting
- TCO Analysis

Use when the user asks for:

- category strategy,
- new category setup,
- supplier consolidation,
- sourcing roadmap,
- management summary,
- transition plan,
- strategic procurement model.

### Supplier performance topic

Primary skill:

- Supplier Scorecard

Supporting skills:

- Supplier Portfolio Review
- Management Procurement Reporting
- Contract Commercial Review

Use when the user asks for:

- supplier evaluation,
- supplier ranking,
- supplier status,
- OTIF,
- complaints,
- supplier review meeting,
- corrective action plan.

### RFQ / RFP preparation

Primary skill:

- RFQ / RFP Preparation

Supporting skills:

- Category Strategy
- Supplier Portfolio Review
- Excel Procurement Analysis
- Management Procurement Reporting

Use when the user asks to:

- prepare RFQ,
- create tender,
- request offers,
- build supplier response matrix,
- define evaluation criteria.

### Supply disruption / delivery delay

Primary skill:

- Supply Disruption Response

Supporting skills:

- Email Procurement Analysis
- Transport Mode Selection
- Order Consolidation
- Supplier Scorecard
- Supplier Counterproposal
- Contract Commercial Review

Use when the user mentions:

- delivery delay,
- supplier cannot meet the date,
- customer is waiting,
- partial delivery,
- quality block,
- capacity shortfall or allocation,
- force majeure,
- expedite.

### Transport / logistics decision

Primary skill:

- Transport Mode Selection

Supporting skills:

- TCO Analysis
- Supply Disruption Response
- Order Consolidation

Use when the user asks:

- which transport mode to use,
- container vs. pallet vs. parcel vs. express vs. air,
- whether expediting pays off,
- whether to split a shipment,
- who pays for expedited transport.

### Customer order completion

Primary skill:

- Order Consolidation

Supporting skills:

- Excel Procurement Analysis
- Supply Disruption Response
- Transport Mode Selection

Use when the user mentions:

- kompletace zakázek,
- customer waiting for a complete delivery,
- open orders with missing lines,
- partial vs. complete shipment,
- allocation of scarce stock between customers.

### Annual supplier productivity

Primary skill:

- Supplier Productivity

Supporting skills:

- Spend Baseline Analysis
- Supplier Portfolio Review
- Negotiation Brief
- Supplier Counterproposal

Use when the user asks for:

- annual productivity request,
- year-on-year price reduction,
- cost-down program,
- annual price review.

### Supplier rebate

Primary skill:

- Supplier Rebate

Supporting skills:

- Contract Commercial Review
- Negotiation Brief
- Excel Procurement Analysis

Use when the user asks about:

- volume or turnover rebate (obratový / odběrový bonus),
- rebate tiers,
- rebate vs. discount,
- rebate settlement or tracking.

## Multi-skill examples

### Example 1: Excel RFQ matrix

Input:
User uploads Excel with supplier offers.

Use:

1. Excel Procurement Analysis
2. Supplier Quotation Comparison
3. TCO Analysis if Incoterms, logistics, MOQ, payment terms or currencies differ
4. Management Procurement Reporting if user needs management output

### Example 2: Supplier email with offer

Input:
Supplier confirms price and terms by email.

Use:

1. Email Procurement Analysis
2. Supplier Quotation Comparison if multiple offers or baseline exist
3. Contract Commercial Review if commercial terms are risky
4. Supplier Counterproposal if a reply is needed

### Example 3: PDF commercial terms

Input:
Supplier sends PDF with terms and conditions.

Use:

1. Document Review Word PDF
2. Contract Commercial Review
3. Supplier Counterproposal if changes should be requested
4. Management Procurement Reporting if approval is needed

### Example 4: New category strategy

Input:
User asks how to strategically manage a new category.

Use:

1. Procurement Category Strategy
2. Spend Baseline Analysis
3. Supplier Portfolio Review
4. Management Procurement Reporting

### Example 5: Supplier performance review

Input:
User gives OTIF, complaints, lead time and spend.

Use:

1. Supplier Scorecard
2. Supplier Portfolio Review
3. Management Procurement Reporting if management decision is required

### Example 6: Supplier delay, customer waiting

Input:
Supplier emails that a delivery will be three weeks late; a key customer is waiting for the parts.

Use:

1. Email Procurement Analysis
2. Supply Disruption Response
3. Transport Mode Selection if expediting is considered
4. Order Consolidation if the customer order contains parts from several suppliers
5. Supplier Scorecard to record the incident

### Example 7: Customer orders waiting for completion

Input:
User provides an open order list where customer orders wait for missing lines from several suppliers.

Use:

1. Excel Procurement Analysis
2. Order Consolidation
3. Supply Disruption Response for late suppliers on blocking lines
4. Transport Mode Selection for urgent blocking lines

### Example 8: Annual supplier negotiation

Input:
User prepares the yearly negotiation with top suppliers.

Use:

1. Spend Baseline Analysis
2. Supplier Productivity
3. Supplier Rebate
4. Negotiation Brief
5. Supplier Counterproposal for the supplier letters

## Output mode routing

Use the correct output level:

### Short

Use when user says:

- stručně,
- manažersky,
- pro vedení,
- executive summary,
- krátce.

Output should be concise and decision-oriented.

### Standard

Use as default.

Output should include structured analysis, risks, recommendation and next steps.

### Detailed

Use when user says:

- detailně,
- kompletní analýza,
- pracovní dokument,
- včetně tabulek,
- připrav podklad.

Output may include detailed tables, assumptions, calculations and action plan.

## Skill reporting rule

When listing used skills:

1. Mention only official skills registered in `skills.yaml`.
2. List the primary skill first.
3. List supporting skills below.
4. Put analytical methods separately.

Example:

Officially used skills:

- Excel Procurement Analysis
- Supplier Quotation Comparison
- TCO Analysis

Analytical steps:

- commercial normalization
- data quality check
- break-even analysis
- risk review

## Missing data handling

If data is incomplete:

1. Continue with available facts.
2. State assumptions clearly.
3. Do not invent missing values.
4. Mark output as conditional.
5. List missing data needed for final decision.

## Default procurement output

Unless a more specific skill requires otherwise, use:

1. Shrnutí
2. Použité skilly
3. Vstupní data
4. Klíčová zjištění
5. Rizika a nejasnosti
6. Doporučení
7. Další kroky

## Rules

- Always choose one primary skill.
- Use supporting skills only when they add value.
- Do not overcomplicate simple requests.
- Do not list analytical steps as official skills.
- Do not make final supplier commitments.
- Do not approve contracts, suppliers or orders without explicit human confirmation.
- Always keep the output practical for procurement use.
