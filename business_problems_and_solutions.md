# Business Problems and Business Solutions

Except Product_Master.csv, Business_Units.csv and Locations.csv, the dataset is modeled/synthetic training data anchored to public products/prices; findings are decision-dashboard evidence, not audited company facts.

This document is for the owner / general manager. It says what is wrong, what to do about it, and how to know it worked. Every figure comes from the current analysis files. Each item is labeled **[computed]** (directly counted), **[scenario]** (depends on an assumption you must confirm), or **[hypothesis]** (needs finance/operations validation before acting on the money value).

Time window for sales figures: October 2023 to September 2026. Inventory snapshots: October 2023 to September 2026.

---

## Problem 1 — Deep wholesale discounts are selling at a loss

**Problem:** A large group of wholesale invoice lines is priced below cost, concentrated in the deepest discount band.

**Evidence:** 4,876 invoice lines with negative profit totaling −1,374,655.95 EGP **[computed]**, denominator: all 180,000 sales lines. All 4,876 are Wholesale (Online: 0, Retail: 0). Of these, 4,754 lines fall in the above-30% discount band. Across 180 channel-month discount cells, 67 breach the floor rule (band margin below 10.40% or any negative-profit rows).

**Why it matters:** 1.37M EGP of realized loss over the window, and the pattern repeats every year (2024: 1,595 lines; 2025: 1,643; 2026 partial: 1,293). Wholesale median margin in the above-30% band is only ~8.4% versus ~41% at zero discount.

**Recommended action:** Sales director to enforce a discount floor: no wholesale deal above 30% without written margin approval, and any band-month that breaches the floor is reviewed before the next price list. Finance to confirm the 10.40% floor number.

**Quick win vs long-term fix:** Quick win: freeze new above-30% wholesale quotes this month. Long-term: contract terms linking discount to volume actually delivered.

**How to measure:** KPI: negative-profit lines per month — direction: down to zero. Second KPI: wholesale gross margin % — direction: up.

**Confidence and limit:** High confidence that the lines and amounts are counted correctly **[computed]**. Limit: cost is estimated, not audited; and "discount causes loss" is association, not proof — costs may also be the driver.

*Source: sales discount-band tables by channel and channel-year; discount-floor alert file (180 month-cells, 67 breached).*

---

## Problem 2 — Too few customers carry the business, and thousands never buy twice

**Problem:** Sales depend on a tiny group of repeat wholesale buyers while thousands of registered customers never purchase and thousands buy only once.

**Evidence:** Top 1% of buying customers take 34.02% of net sales; top 5% take 79.74%; top 10% take 87.00% **[computed]**, denominator: customers with at least one invoice. 4,026 customers bought exactly once; 4,366 registered customers never purchased at all **[computed]**.

**Why it matters:** Losing a handful of top accounts would remove a double-digit share of revenue. The 4,366 never-buyers and 4,026 one-time buyers are the cheapest growth available — reactivation costs less than acquisition.

**Recommended action:** Sales manager to assign the top 50 accounts a named owner with a quarterly review. Marketing to run a win-back campaign for one-time buyers within 60 days of first purchase, and an onboarding offer for registered-never-bought accounts.

**Quick win vs long-term fix:** Quick win: call the top 20 accounts this month and the 4,366 dormant accounts by email/SMS. Long-term: repeat-purchase program and account-level pricing.

**How to measure:** KPI: share of sales from repeat buyers — direction: up. Second KPI: one-time-buyer conversion rate — direction: up.

**Confidence and limit:** High confidence on counts and shares **[computed]**. Limit: the data cannot say *why* customers do not return (price, fit, service); do not assume a cause before asking them.

*Source: customer concentration table (25,634 buyers ranked); customer metrics.*

---

## Problem 3 — Cash is trapped in overstock in two warehouses while the third stocks out

**Problem:** At the same time, some locations hold far more stock than they sell while another location keeps running out.

**Evidence:** 1,958 location-product-month rows above 180 days of cover (30.73% of 6,372 inventory rows); 939 rows above 365 days **[scenario: threshold rule]**. In the latest month (September 2026), 40 overstock rows hold 46,867 units, scenario value 7,030,050 EGP at the assumed 150 EGP/unit **[scenario]**. Stockouts: 147 rows with stockout days, 150 rows at zero stock, 141 of the 147 stockout rows sit in a single location (LOC003). Overstock units concentrate in LOC002 and LOC001.

**Why it matters:** Working capital is frozen in slow stock (about 7M EGP under the scenario assumption) while stockouts in LOC003 mean lost sales on fast movers — the worst combination: cash trapped *and* sales missed.

**Recommended action:** Operations manager to run a monthly rebalance: transfer list from LOC001/LOC002 overstock (top products P023, P019, P041, P054) to cover LOC003 gaps before placing new purchase orders. Purchasing to freeze replenishment of any product-location above 365 days of cover until it drops below 180.

**Quick win vs long-term fix:** Quick win: one transfer order this month for the 7 latest stockout products. Long-term: per-location reorder points and a 30/60/90-day demand forecast.

**How to measure:** KPI: overstock rows above 180 days — direction: down. Second KPI: stockout days per month in LOC003 — direction: down.

**Confidence and limit:** High confidence on row counts and unit counts **[computed]**; the 180/365-day rule and the 150 EGP/unit value are **[scenario]** assumptions finance must approve. Limit: Days of Cover is a stored field, not independently recomputed; transfer feasibility (transport, handling) is not in the data.

*Source: overstock-watch file (1,958 rows) and stockout file (147 rows); latest-snapshot and cover-rule tables.*

---

## Problem 4 — Quality losses concentrate in two production stages

**Problem:** Rejected output costs about 16.3M EGP in estimated loss, led by the Cutting and Finishing stages.

**Evidence:** Total QC estimated loss 16,322,914.13 EGP **[computed]**, denominator: all 9,000 QC inspections, window 2023-10 to 2026-09. By stage: Cutting 2,810,109.57, Finishing 2,791,198.60, Sewing 2,699,704.48 **[computed]**. Reject rate across 161 line-month cells with meaningful volume ranges 1.69% to 3.34% (median 2.50%) — a spread, not one bad line.

**Why it matters:** Cutting alone represents roughly 17% of total QC loss; a one-point reject reduction there is worth hundreds of thousands of EGP. The spread pattern means improvement methods can be copied from better cells to worse ones.

**Recommended action:** Factory manager to audit Cutting stations first (blades, markers, operator training), then Finishing. Quality to publish a monthly reject-rate league table per line-month and review the worst 3 cells every month.

**Quick win vs long-term fix:** Quick win: Cutting corrective action this month. Long-term: stage-level loss budgets tied to supervisor KPIs.

**How to measure:** KPI: reject rate per line-month — direction: down toward the 1.69% best cells. Second KPI: QC estimated loss per quarter — direction: down.

**Confidence and limit:** Medium-high confidence **[computed]** on counted rejects; the EGP loss is *estimated* from modeled data, so treat it as a pointer to where to look, not an audited cost. Limit: the stored Efficiency % field could not be reproduced by any tested formula and is not used here.

*Source: quality-by-stage table; line-month reject table.*

---

## Problem 5 — Machines stop too often for the same reason, and 1 in 6 orders ships late

**Problem:** Unplanned stops total 6,173.7 hours, led by mechanical faults, and 407 of 2,500 production orders (16.28%) finished late.

**Evidence:** Downtime 6,173.7 hours **[computed]**. By reason: mechanical fault 1,530.9h, setup/changeover 1,284.8h, planned maintenance 1,224.5h **[computed]**. Late orders: 407 of 2,500 (16.28%) **[computed]**; late orders carry 14.43 overtime hours per order versus 5.62 for on-time orders. Plan attainment overall is 90.87%.

**Why it matters:** Mechanical faults alone exceed total planned maintenance — prevention is cheaper than breakdowns. Late orders burn overtime (2.5x the hours) and risk wholesale customer penalties and churn among the concentrated top accounts (see Problem 2).

**Recommended action:** Maintenance manager to put the worst machines on preventive schedule starting with mechanical-fault history; production planner to protect capacity for the top wholesale SKUs so their orders do not go late.

**Quick win vs long-term fix:** Quick win: preventive checklist on the top-3 fault machines. Long-term: spare-parts stocking and setup-time reduction program.

**How to measure:** KPI: mechanical-fault hours per month — direction: down. Second KPI: late-order rate — direction: down from 16.28%.

**Confidence and limit:** High confidence on hours and late counts **[computed]**. Limit: the bottleneck field is only filled for a subset of orders and must not be read as a factory-wide share.

*Source: downtime-by-machine-reason table; late-vs-on-time orders table.*

---

## Problem 6 — Returns are a sizing problem, not a factory problem

**Problem:** The top return reason is size/fit, concentrated in Online sales — while the data shows essentially no link between returns and factory rejects.

**Evidence:** Size/fit: 13,899 returned units across 3,050 rows, about 37% of all 37,233 returned units **[computed]**, denominator: returned units. Size/fit share within channel: Online 35.3%, Retail 35.8%, Wholesale 38.0%. Overall return rates: 4.75% of rows, 2.24% of units, 2.24% of value **[computed]**. Product-level correlation between return rate and QC reject rate: r = 0.017 (classified weak) **[computed]**, 59 products in both aggregates.

**Why it matters:** Returns cost refunds plus handling (size/fit refunds in Online alone exceed 840,000 EGP in the window), and Online has the highest return-row rate (about 7.7% of rows vs ~1.8% in Wholesale). Blaming production would waste effort: r = 0.017 means fixing QC will not move returns.

**Recommended action:** E-commerce manager to add real size guides, fit notes per product family (Pajamas/Homewear leads size/fit returns), and fit-predictor questions at checkout. Customer service to log "size guidance" tickets against product pages monthly.

**Quick win vs long-term fix:** Quick win: size-guide content on the top-10 returned SKUs. Long-term: standardized sizing blocks across families and a fit-based recommendation.

**How to measure:** KPI: Online size/fit return units per month — direction: down. Second KPI: Online return-row rate — direction: down from ~7.7%.

**Confidence and limit:** High confidence on return counts and the weak correlation **[computed]**. Limit: return quantities assume full-line returns as recorded; the data cannot prove *why* a customer picked the wrong size.

*Source: returns-by-reason/channel tables; returns-vs-QC product join (r = 0.017); channel-mix table.*

---

## Problem 7 — Suppliers are often late, two materials bypass the BOM, and the money does not reconcile (finance job first)

**Problem:** More than a third of purchase orders arrive late, two purchased materials do not appear in any product recipe, and total purchase spend is roughly double sales — which cannot be a real cost ratio and must be reconciled by finance before any savings claim.

**Evidence:** Late-PO rate 34.64% **[computed]**, denominator: 3,600 POs. Worst: SUP09 late on 65.4% of its 289 POs (avg 3.63 days late); SUP04 late on 60.1% of 281 POs (avg 2.95 days) **[computed]**. Two materials bought but absent from the BOM: Elastic Band (279 POs, 84,809,138.95 EGP ordered) and Carton Box (310 POs, 10,910,652.85 EGP ordered) **[computed]**. Accepted PO spend 869,566,469.42 EGP is 2.06x net sales and 2.44x estimated COGS **[hypothesis — unreconciled]**.

**Why it matters:** Late materials put production orders at risk of lateness (Problem 5 tracks the 16.28% late-order rate separately — the data does not prove how many late orders each late PO caused). The two off-BOM materials total ~95.7M EGP of ordered spend that no recipe explains — possible data-unit mismatch, or real off-spec buying. The 869M figure must NOT be quoted as company spend until finance reconciles units and timing.

**Recommended action:** Procurement to (a) put SUP09 and SUP04 on a delivery-improvement plan with penalties, (b) explain or stop the two off-BOM materials with the factory within 30 days. Finance controller to reconcile PO units vs BOM consumption units and confirm the true spend-to-COGS ratio.

**Quick win vs long-term fix:** Quick win: delivery plan for SUP09/SUP04 and a hold on off-BOM POs. Long-term: supplier scorecard with on-time delivery tied to contract renewal (the 432-row monthly scorecard already exists for this).

**How to measure:** KPI: late-PO rate — direction: down from 34.64%. Second KPI: off-BOM ordered spend — direction: down to zero or explained.

**Confidence and limit:** High confidence on late counts and off-BOM identification **[computed]**. The 869M spend scale is **[hypothesis]** — modeled quantities that likely mix procurement/stocking scale with timing effects; do not present it as a savings pool.

*Source: supplier score tables and monthly scorecard (432 rows); off-BOM detail table; scale-reconciliation tables.*

---

## Problem 8 — Marketing numbers look better than reality and cannot guide the budget yet

**Problem:** Reported attributed revenue is more than five times online sales, which is impossible as a true sales contribution — the attribution method must be clarified before spending one more pound on its basis.

**Evidence:** Marketing spend 14,583,976.00 EGP; attributed revenue 179,741,957.27 EGP; ROAS 12.32 **[computed]**. Attributed revenue averages 584.00% of online net sales by month (mean of 36 monthly ratios, variation 0.70); total attributed divided by total online net sales is 550.86% (5.5x) **[computed/hypothesis — modeled attribution]**. Web conversion overall is 2.83% (47,462 orders from 1,678,059 sessions) **[computed]**.

**Why it matters:** A 12.3 ROAS will be quoted to justify bigger budgets, but money attributed at 5.5x the online sales base cannot all be real incremental sales. Acting on it risks overspending on the wrong platforms.

**Recommended action:** Marketing manager to freeze budget shifts until the attribution method is documented (what counts as "attributed", over what window, vs web sessions and online orders in the monthly reconciliation table). Keep marketing as an efficiency screen only: track ROAS and conversion by platform, decide with online-base share, all-channel share, or both — but as ratios to watch, not profit earned.

**Quick win vs long-term fix:** Quick win: this-month platform review using the efficiency table with the limitation attached. Long-term: proper incrementality test agreed with finance.

**How to measure:** KPI: web conversion rate — direction: up from 2.83%. Budget decisions stay on hold until the attribution question is answered.

**Confidence and limit:** High confidence on spend, sessions, orders **[computed]**; the attributed-revenue column is **[hypothesis]** modeled data. Limit: no causal claim is possible from this data — nothing here proves marketing caused any sale.

*Source: marketing efficiency and platform-month tables; web/month table; monthly reconciliation table.*

---

## Top-5 priority list (ranked by EGP impact x ease x confidence)

1. **Enforce the wholesale discount floor** (Problem 1) — stops a counted 1.37M EGP bleed; a policy decision, no investment; computed data.
2. **Fix size/fit for Online** (Problem 6) — 13,899 returned units and 840k+ EGP Online size/fit refunds; content fix, fast; computed data.
3. **Rebalance LOC001/LOC002 overstock into LOC003** (Problem 3) — frees working capital (scenario ~7M EGP) and recovers lost sales; one transfer cycle; counts are computed, only the EGP value is scenario.
4. **Preventive maintenance on mechanical faults** (Problem 4/5) — 1,531 fault hours feeding 16.28% late orders and 2.5x overtime; computed data.
5. **Win back one-time and never-bought customers** (Problem 2) — 8,392 reachable customers against an 87%-concentrated base; computed data.

## Do NOT conclude this from this data

- Do not quote ROAS 12.3 or 584%/550.86% as proof marketing works — attributed revenue exceeds online sales; the method is unverified.
- Do not quote 869M EGP as company purchasing spend or a savings pool — it is unreconciled with sales/COGS **[hypothesis]**.
- Do not sum Closing_Stock across months (2,312,112 unit-months) and call it stock on hand — on-hand stock is the latest month only: 77,867 units.
- Do not use the stored Efficiency % field for any decision — it matches none of the tested formulas.
- Do not blame production quality for returns — product-level correlation is r = 0.017 (no link).
- Do not read deep discounts as the proven *cause* of losses — they coincide with losses; cost levels may contribute.
- Do not treat the 150 EGP/unit overstock value (7,030,050 EGP) as a balance-sheet figure — it is a scenario awaiting a finance-approved unit cost.
- Do not read the bottleneck field as a factory-wide problem share — it is filled only for a subset of orders.

## Decisions the client must make

1. Overstock rule: confirm **above 180 days = watch, above 365 = severe** (replacing the old above-90 rule that flagged 51.84% of rows).
2. Discount floor: confirm the rule **band margin below 10.40% (total margin minus 5 points) or any negative-profit rows = breach**, and who approves exceptions.
3. Unit cost: replace the **150 EGP/unit scenario assumption** with a finance-approved cost source (or approve 150).
4. Marketing reporting: show **online-base share, all-channel share, or both** — and order a written attribution-method note before any budget decision.
5. Dictionary hygiene: **supply Sources.csv or remove it** from the data dictionary (Case_Briefs.csv and Data_Dictionary.csv are helper files without dictionary entries — accepted as-is unless you object).
6. Supplier action: approve the **delivery-improvement plan for SUP09 and SUP04** and the hold/explanation on the **two off-BOM materials**.

## 30 / 60 / 90 day action plan

**Days 1–30 (stop the bleeding):**
- Freeze new above-30% wholesale quotes without margin sign-off (owner → sales director).
- One transfer order: LOC001/LOC002 overstock to LOC003 stockouts (owner → operations).
- Size guides live on top-10 returned SKUs (owner → e-commerce).
- Preventive checklist on top-3 fault machines (owner → maintenance).
- Call top-20 accounts; message 4,366 dormant registered customers (owner → sales/marketing).

**Days 31–60 (make it systematic):**
- Monthly discount-floor review using the 180-cell breach file (finance + sales).
- Monthly reject league table per line-month starting with Cutting (factory + quality).
- Supplier delivery plans signed for SUP09/SUP04; off-BOM materials explained or stopped (procurement).
- Attribution-method note delivered by marketing; budgets stay frozen until then.
- Finance delivers PO-vs-BOM unit reconciliation and the approved unit cost.

**Days 61–90 (lock the gains):**
- Contract terms: discount tied to delivered volume; late-delivery penalties active.
- Reorder points per location-product live; first 30/60/90-day demand forecast reviewed.
- Repeat-purchase program for converted one-time buyers; review KPIs: negative-profit lines → 0, stockout days in LOC003 → down, late-order rate down from 16.28%, Online size/fit returns down, late-PO rate down from 34.64%.
