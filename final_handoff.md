# Final Handoff After Phase 4
Except Product_Master.csv, Business_Units.csv and Locations.csv, the dataset is modeled/synthetic training data anchored to public products/prices; findings are decision-dashboard evidence, not audited company facts.
## Files Created
| File | Rows / items | Purpose |
| --- | ---: | --- |
| outputs/p1_data_health.md | Markdown report | Phase 1 data health, grains, keys, dates, derived checks and ranked problems |
| outputs/p2b_grain_proof.md | 75 table checks | Current table grain proof and archived fan-out explanation |
| outputs/metrics.json | 57 metrics | Flat metrics list for dashboard ingestion |
| outputs/p2_findings.md | Markdown report | Ranked findings with evidence, grain, denominator, type tag and limitation |
| outputs/p3_recheck.md | 57 rechecks | Independent headline metric recomputation and synthetic flags |
| outputs/tables/case_brief_stage_map.csv | 8 | Detailed stage table for charting |
| outputs/tables/customer_service_by_month_channel_issue.csv | 1,122 | Detailed stage table for charting |
| outputs/tables/dictionary_file_reconciliation.csv | 3 | Detailed stage table for charting |
| outputs/tables/group_operations_by_business_unit_month.csv | 180 | Detailed stage table for charting |
| outputs/tables/inventory_cover_rule_explanation.csv | 1 | Detailed stage table for charting |
| outputs/tables/inventory_demand_backtest_by_location.csv | 8 | Detailed stage table for charting |
| outputs/tables/inventory_demand_baseline_backtest.csv | 2 | Detailed stage table for charting |
| outputs/tables/inventory_family_month.csv | 144 | Detailed stage table for charting |
| outputs/tables/inventory_latest_snapshot.csv | 177 | Detailed stage table for charting |
| outputs/tables/inventory_location_cover_by_year.csv | 65 | Detailed stage table for charting |
| outputs/tables/inventory_location_latest_vs_unit_months.csv | 3 | Detailed stage table for charting |
| outputs/tables/inventory_location_product_month.csv | 6,372 | Detailed stage table for charting |
| outputs/tables/inventory_vs_sales_units_product_month_location.csv | 6,372 | Detailed stage table for charting |
| outputs/tables/marketing_attribution_share_stability.csv | 1 | Detailed stage table for charting |
| outputs/tables/marketing_efficiency_by_platform.csv | 5 | Detailed stage table for charting |
| outputs/tables/marketing_platform_month.csv | 152 | Detailed stage table for charting |
| outputs/tables/marketing_web_sales_reconciliation_month.csv | 36 | Detailed stage table for charting |
| outputs/tables/production_downtime_machine_month_reason.csv | 1,657 | Detailed stage table for charting |
| outputs/tables/production_efficiency_reproduction_check.csv | 5 | Detailed stage table for charting |
| outputs/tables/production_late_vs_ontime_orders.csv | 2 | Detailed stage table for charting |
| outputs/tables/production_line_month.csv | 180 | Detailed stage table for charting |
| outputs/tables/production_printing_downtime_machine_month_join.csv | 432 | Detailed stage table for charting |
| outputs/tables/production_printing_machine_month.csv | 671 | Detailed stage table for charting |
| outputs/tables/production_quality_stage_product_month.csv | 8,353 | Detailed stage table for charting |
| outputs/tables/returns_by_channel_family_product_month_reason.csv | 12,729 | Detailed stage table for charting |
| outputs/tables/returns_channel_family_rates.csv | 12 | Detailed stage table for charting |
| outputs/tables/returns_reason_by_channel.csv | 18 | Detailed stage table for charting |
| outputs/tables/returns_row_vs_unit_rate_explanation.csv | 1 | Detailed stage table for charting |
| outputs/tables/returns_vs_qc_product_join.csv | 59 | Detailed stage table for charting |
| outputs/tables/sales_by_governorate_channel.csv | 39 | Detailed stage table for charting |
| outputs/tables/sales_by_month_channel.csv | 108 | Detailed stage table for charting |
| outputs/tables/sales_by_year_month_channel_family_product_discount.csv | 17,881 | Detailed stage table for charting |
| outputs/tables/sales_channel_mix_by_year.csv | 12 | Detailed stage table for charting |
| outputs/tables/sales_customer_concentration.csv | 25,634 | Detailed stage table for charting |
| outputs/tables/sales_discount_behavior_by_channel.csv | 9 | Detailed stage table for charting |
| outputs/tables/sales_discount_behavior_by_channel_year.csv | 36 | Detailed stage table for charting |
| outputs/tables/sales_discount_relationship_by_channel.csv | 9 | Detailed stage table for charting |
| outputs/tables/sales_family_concentration.csv | 4 | Detailed stage table for charting |
| outputs/tables/sales_margin_bands_by_channel_year.csv | 48 | Detailed stage table for charting |
| outputs/tables/sales_top1pct_customer_type_mix.csv | 1 | Detailed stage table for charting |
| outputs/tables/supply_bought_not_bom_detail.csv | 2 | Detailed stage table for charting |
| outputs/tables/supply_material_coverage.csv | 12 | Detailed stage table for charting |
| outputs/tables/supply_scale_reconciliation_by_material.csv | 12 | Detailed stage table for charting |
| outputs/tables/supply_scale_reconciliation_summary.csv | 1 | Detailed stage table for charting |
| outputs/tables/supply_supplier_material_month.csv | 2,571 | Detailed stage table for charting |
| outputs/tables/supply_supplier_performance.csv | 12 | Detailed stage table for charting |
| outputs/tables/supply_supplier_rank_stability.csv | 12 | Detailed stage table for charting |
| outputs/tables/supply_supplier_score_overall.csv | 12 | Detailed stage table for charting |
| outputs/tables/web_month.csv | 36 | Detailed stage table for charting |
| outputs/alerts/discount_floor_breach.csv | 180 | Automation alert/feed file |
| outputs/alerts/overstock_watch.csv | 1,958 | Automation alert/feed file |
| outputs/alerts/returns_pareto.csv | 757 | Automation alert/feed file |
| outputs/alerts/stockout_new.csv | 147 | Automation alert/feed file |
| outputs/alerts/summary.json | JSON object | Automation alert/feed file |
| outputs/alerts/supplier_scorecard.csv | 432 | Automation alert/feed file |

## 10 Most Important Findings
| # | Type | Stage | Finding | Evidence | Limitation |
| ---: | --- | --- | --- | --- | --- |
| 1 | hypothesis | SUPPLY | Data problem #1: supply EGP scale is unreconciled with sales and COGS | Accepted PO spend is 2.06x recomputed net sales and 2.44x estimated COGS. Material-level purchased quantities are compared to BOM-implied production requirements in supply_scale_reconciliation_by_material.csv. Most likely hypothesis: modeled PO quantities represent procurement/replenishment or timing/stocking scale, not consumption matched to finished-goods sales COGS. | All supply EGP metrics are marked unreconciled with sales/COGS until units and timing are resolved. |
| 2 | computed | SUPPLY | Bought materials outside BOM need review | 2 material IDs were bought but do not appear in Product_BOM; their PO count and ordered spend are in supply_bought_not_bom_detail.csv. | Modeled/synthetic table unless noted. |
| 3 | hypothesis | SUPPLY | Supplier spend ranking is auditable but EGP is unreconciled | SUP07 is roughly flat versus the next item: top 83,379,175.23, next 81,609,056.08, average 72,463,872.45. Ranking stability is in supply_supplier_rank_stability.csv. Treat EGP as unreconciled with sales/COGS. | Supply EGP scale is unreconciled with sales/COGS. |
| 4 | scenario | INVENTORY | Latest overstock has scenario value only | Latest overstock units are valued with explicit 150.00 EGP/unit assumption in metrics and inventory tables. | Scenario value, not a sourced cost. |
| 5 | computed | PRODUCTION | QC estimated loss is the largest operating EGP signal | Cutting is roughly flat versus the next item: top 2,810,109.57, next 2,791,198.60, average 2,720,485.69. | EGP is estimated loss from modeled Quality.csv. |
| 6 | computed | SALES | Negative-profit exposure is concentrated in discount behavior | Negative-profit rows total 4,876 with recomputed loss -1,374,655.95 EGP. The discount-band table reports totals by channel/year/band so no total is labeled as a single band. | Modeled/synthetic table unless noted. |
| 7 | computed | RETURNS | Return reasons are checked for Pareto shape | Size / fit leads the next item by 7,868.00 and is 7,693.50 above the average. | Modeled/synthetic table unless noted. |
| 8 | scenario | INVENTORY | Old >90-day cover rule was too broad for this modeled panel | The old >90-day rule flags 3,303 rows (51.84%); the 180-day watch rule flags 1,958 rows (30.73%) and >365-day severe rule flags 939 rows (14.74%). | Threshold rule is a dashboard scenario rule. |
| 9 | computed | PRODUCTION | Downtime reasons are compared against next and average | Mechanical fault leads the next item by 246.10 and is 501.95 above the average. | Modeled/synthetic table unless noted. |
| 10 | hypothesis | MARKETING/WEB | Marketing attribution is compared against online sales base | Attributed revenue averages 584.00% of online net sales by month with coefficient of variation 0.70. The 584% figure is the monthly average of ratios; total attributed revenue divided by total online net sales is 550.86% (5.5x). The gap is a mean-of-ratios effect and both figures exceed online sales, so this is a data/model limitation, not a business insight. All-channel share is context only. No causal claim is made. | Attribution is modeled; correct comparison base is online channel net sales, not all-channel revenue. Attributed revenue exceeds online sales, so shares cannot be used for budget decisions until the attribution method is clarified. |

## Data Problems That Limit Findings
- 1. Severity 3 | affects Supply | Purchase_Orders.csv: accepted PO spend is unreconciled with sales/COGS scale; all supply EGP metrics remain hypothesis/unreconciled until unit and timing assumptions are resolved.
- 2. Severity 3 | affects Inventory | derived-column: inventory Closing_Stock = Opening + Received - Sold + Returned - Damaged has 147 mismatches.
- 3. Severity 3 | affects Marketing/Web | derived-column: web Conversion_Rate = Orders / Sessions has 9 mismatches.
- 4. Severity 3 | affects Understand | Case_Briefs.csv: File is not listed in Data_Dictionary.csv.
- 5. Severity 3 | affects Understand | Data_Dictionary.csv: File is not listed in Data_Dictionary.csv.
- 6. Severity 3 | affects Understand | Sources.csv: Dictionary entry without file; confirm whether Sources.csv should be supplied or removed from Data_Dictionary.csv.
- 7. Severity 2 | affects All | Production_Orders.csv: High-null columns may be subset-only fields: Primary_Bottleneck (83.72%).
- 8. Severity 2 | affects All | Sales_Transactions.csv: High-null columns may be subset-only fields: Return_Date (95.25%).

## Decisions Needed
- Confirm whether Sources.csv should be supplied or removed from Data_Dictionary.csv. Current reconciliation: Sources.csv is in the dictionary but no file exists; Case_Briefs.csv and Data_Dictionary.csv are helper/control files without dictionary entries.
- Confirm the dashboard threshold for overstock. Phase 4 now uses the addendum rule of Days_of_Cover > 180, with >365 shown as severe.
- Confirm the dashboard threshold for discount-floor alerts. Phase 4 flags bands below total gross margin minus 5 percentage points or any negative-profit rows.
- Marketing is kept as an efficiency/reconciliation screen only per addendum. Decide only whether to show online-base attributed share, all-channel context share, or both.
- Confirm whether the overstock scenario unit-cost assumption of 150.00 EGP should be replaced by a finance-approved cost source.

## Verification
- scripts/p2b_grain_proof.py checked 75 current non-versioned tables and found 0 grain failures.
- scripts/p3_recheck.py recomputed 57 headline metrics and found 0 mismatches against outputs/metrics.json.
- Raw CSV files were read only. Generated files were written under outputs/ with backups made before overwrites.
