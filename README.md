# Delivery README — Sharnouby Business Analytics (Task 2)

Except Product_Master.csv, Business_Units.csv and Locations.csv, the dataset is modeled/synthetic training data anchored to public products/prices; findings are decision-dashboard evidence, not audited company facts.

## What is in this package

- `business_problems_and_solutions.md` — 8 business problems and actions in plain language, top-5 priorities, 30/60/90-day plan. **Start here.**
- `final_handoff.md` — technical handoff: files created, top-10 findings with limitations, data problems, decisions needed, verification.
- `p1_data_health.md` — Phase 1 data health (grains, keys, dates, derived checks, 8 ranked problems).
- `p2_findings.md` — Phase 2 ranked findings (14, each with type tag, grain, denominator, size, limitation).
- `p2b_grain_proof.md` — grain proof: 75 table checks, 0 failures.
- `p3_recheck.md` — independent recomputation: 57 metrics, 0 mismatches.
- `metrics.json` — 57 headline metrics (list of {id, value, unit, grain, denominator, type, assumption}).
- `tables/` — 49 detail tables for charting.
- `numbers_book/` — 27 per-entity 360 tables + `NUMBERS_BOOK.md`.
- `alerts/` — 5 alert files + `summary.json`.
- `dashboard-dist/` — built interactive dashboard (static site). Serve the folder over HTTP
  (e.g. `python -m http.server` inside it) and open `index.html`; it loads `data/dashboard-data.json`
  (57 metrics + tables + alerts + embedded reports, regenerated at delivery).

## Definitions and threshold log (confirm these)

- Overstock watch: `Days_of_Cover > 180`; severe: `> 365` (replaces the old `> 90` rule, which flagged 51.84% of rows).
- Overstock value: **scenario only**, 150.00 EGP/unit × 46,867 latest-month overstock units = 7,030,050 EGP. Replace with a finance-approved unit cost.
- Stockout: `Stockout_Days_In_Month > 0` = 147 rows; `Closing_Stock == 0` = 150 rows; overlap = 147 rows. Reported separately, never merged.
- Marketing: 584.00% = monthly average of (attributed / online net sales) ratios; 550.86% (5.5x) = total attributed / total online net sales. Both exceed online sales — a data/model limitation, not a business insight. No causal claims.
- Units vs unit-months: latest-month stock = **units** (77,867); sums over monthly snapshots = **unit-months** (2,312,112). Never read unit-months as stock on hand.
- Supply EGP (869,566,469.42 accepted spend, 2.06x net sales) is **hypothesis / unreconciled** until finance resolves units and timing. Not a savings pool.
- Sales window: 2023-10-01 to 2026-09-30. Net sales 421,338,377.53 EGP; gross margin 15.40% (COGS estimated).

## Verification (reproduced at delivery)

- `p2_metrics.py` → 48 metrics + `p5_numbers_book.py` appends 9 → `metrics.json` = 57.
- `p2b_grain_proof.py` → 75 checks, 0 failures. `grain_registry.csv` is the control registry, excluded from checks.
- `p3_recheck.py` → 57 recomputed, 0 mismatches. Separate code path, shared I/O helpers only.
- Raw CSVs were read only, never modified.
