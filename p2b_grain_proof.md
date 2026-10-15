# Phase 2B Grain Proof

Except Product_Master.csv, Business_Units.csv and Locations.csv, the dataset is modeled/synthetic training data anchored to public products/prices; findings are decision-dashboard evidence, not audited company facts.

Every non-versioned CSV in outputs/tables/ is checked as row count equals distinct stated grain keys. Numbers-book CSVs listed in outputs/numbers_book/grain_registry.csv are checked the same way.

## Result
- Tables checked: 75
- Failed checks: 0
- outputs/numbers_book/grain_registry.csv is the control registry for numbers-book grains and is excluded from the grain checks.
- Fan-out proof passes when rows equal distinct grain-key combinations.

## Table Checks
| File | Stated grain key | Rows | Distinct grain keys | Pass | Note |
| --- | --- | ---: | ---: | --- | --- |
| outputs\tables\case_brief_stage_map.csv | dashboard_stage | 8 | 8 | yes | no fan-out |
| outputs\tables\customer_service_by_month_channel_issue.csv | month + Channel + Issue_Type | 1,122 | 1122 | yes | no fan-out |
| outputs\tables\dictionary_file_reconciliation.csv | check + file | 3 | 3 | yes | no fan-out |
| outputs\tables\group_operations_by_business_unit_month.csv | month + Business_Unit + Primary_KPI | 180 | 180 | yes | no fan-out |
| outputs\tables\inventory_cover_rule_explanation.csv | old_rule + new_watch_rule + severe_rule | 1 | 1 | yes | no fan-out |
| outputs\tables\inventory_demand_backtest_by_location.csv | scope + method | 8 | 8 | yes | no fan-out |
| outputs\tables\inventory_demand_baseline_backtest.csv | model | 2 | 2 | yes | no fan-out |
| outputs\tables\inventory_family_month.csv | month + Product_Family | 144 | 144 | yes | no fan-out |
| outputs\tables\inventory_latest_snapshot.csv | Snapshot_Month + Location_ID + Product_ID | 177 | 177 | yes | no fan-out |
| outputs\tables\inventory_location_cover_by_year.csv | year + Location_ID + cover_band | 65 | 65 | yes | no fan-out |
| outputs\tables\inventory_location_latest_vs_unit_months.csv | Location_ID | 3 | 3 | yes | no fan-out |
| outputs\tables\inventory_location_product_month.csv | month + Location_ID + Product_ID | 6,372 | 6372 | yes | no fan-out |
| outputs\tables\inventory_vs_sales_units_product_month_location.csv | Product_ID + month + Location_ID | 6,372 | 6372 | yes | no fan-out |
| outputs\tables\marketing_attribution_share_stability.csv | note | 1 | 1 | yes | no fan-out |
| outputs\tables\marketing_efficiency_by_platform.csv | Platform | 5 | 5 | yes | no fan-out |
| outputs\tables\marketing_platform_month.csv | month + Platform | 152 | 152 | yes | no fan-out |
| outputs\tables\marketing_web_sales_reconciliation_month.csv | month | 36 | 36 | yes | no fan-out |
| outputs\tables\production_downtime_machine_month_reason.csv | month + Machine_ID + Reason + Planned | 1,657 | 1657 | yes | no fan-out |
| outputs\tables\production_efficiency_reproduction_check.csv | formula_tested | 5 | 5 | yes | no fan-out |
| outputs\tables\production_late_vs_ontime_orders.csv | late | 2 | 2 | yes | no fan-out |
| outputs\tables\production_line_month.csv | month + Line_ID | 180 | 180 | yes | no fan-out |
| outputs\tables\production_printing_downtime_machine_month_join.csv | month + Machine_ID | 432 | 432 | yes | no fan-out |
| outputs\tables\production_printing_machine_month.csv | month + Machine_ID + Print_Type | 671 | 671 | yes | no fan-out |
| outputs\tables\production_quality_stage_product_month.csv | month + Stage + Product_ID + Defect_Type | 8,353 | 8353 | yes | no fan-out |
| outputs\tables\returns_by_channel_family_product_month_reason.csv | month + Channel + Product_Family + Product_ID + Return_Reason | 12,729 | 12729 | yes | no fan-out |
| outputs\tables\returns_channel_family_rates.csv | Channel + Product_Family | 12 | 12 | yes | no fan-out |
| outputs\tables\returns_reason_by_channel.csv | Channel + Return_Reason | 18 | 18 | yes | no fan-out |
| outputs\tables\returns_row_vs_unit_rate_explanation.csv | explanation | 1 | 1 | yes | no fan-out |
| outputs\tables\returns_vs_qc_product_join.csv | Product_ID | 59 | 59 | yes | no fan-out |
| outputs\tables\sales_by_governorate_channel.csv | Customer_Governorate + Channel | 39 | 39 | yes | no fan-out |
| outputs\tables\sales_by_month_channel.csv | month + Channel | 108 | 108 | yes | no fan-out |
| outputs\tables\sales_by_year_month_channel_family_product_discount.csv | year + month + Channel + Product_Family + Product_ID + discount_band | 17,881 | 17881 | yes | no fan-out |
| outputs\tables\sales_channel_mix_by_year.csv | year + Channel | 12 | 12 | yes | no fan-out |
| outputs\tables\sales_customer_concentration.csv | Customer_ID | 25,634 | 25634 | yes | no fan-out |
| outputs\tables\sales_discount_behavior_by_channel.csv | Channel + discount_band | 9 | 9 | yes | no fan-out |
| outputs\tables\sales_discount_behavior_by_channel_year.csv | year + Channel + discount_band | 36 | 36 | yes | no fan-out |
| outputs\tables\sales_discount_relationship_by_channel.csv | Channel + discount_band | 9 | 9 | yes | no fan-out |
| outputs\tables\sales_family_concentration.csv | Product_Family | 4 | 4 | yes | no fan-out |
| outputs\tables\sales_margin_bands_by_channel_year.csv | year + Channel + margin_band | 48 | 48 | yes | no fan-out |
| outputs\tables\sales_top1pct_customer_type_mix.csv | customer_type | 1 | 1 | yes | no fan-out |
| outputs\tables\supply_bought_not_bom_detail.csv | Material_ID | 2 | 2 | yes | no fan-out |
| outputs\tables\supply_material_coverage.csv | material_id | 12 | 12 | yes | no fan-out |
| outputs\tables\supply_scale_reconciliation_by_material.csv | Material_ID + Unit | 12 | 12 | yes | no fan-out |
| outputs\tables\supply_scale_reconciliation_summary.csv | hypothesis | 1 | 1 | yes | no fan-out |
| outputs\tables\supply_supplier_material_month.csv | month + Supplier_ID + Material_ID | 2,571 | 2571 | yes | no fan-out |
| outputs\tables\supply_supplier_performance.csv | Supplier_ID | 12 | 12 | yes | no fan-out |
| outputs\tables\supply_supplier_rank_stability.csv | Supplier_ID | 12 | 12 | yes | no fan-out |
| outputs\tables\supply_supplier_score_overall.csv | Supplier_ID | 12 | 12 | yes | no fan-out |
| outputs\tables\web_month.csv | month | 36 | 36 | yes | no fan-out |
| outputs\numbers_book\channel_360.csv | Channel | 3 | 3 | yes | no fan-out |
| outputs\numbers_book\channel_360_by_year.csv | year + Channel | 12 | 12 | yes | no fan-out |
| outputs\numbers_book\channel_margin_bands.csv | Channel + margin_band | 12 | 12 | yes | no fan-out |
| outputs\numbers_book\column_profiles.csv | file + column | 72 | 72 | yes | no fan-out |
| outputs\numbers_book\customer_deciles.csv | decile | 10 | 10 | yes | no fan-out |
| outputs\numbers_book\customer_segments.csv | Customer_Type + Governorate + Age_Band + Gender + Acquisition_Channel + Consent_Status | 1,877 | 1877 | yes | no fan-out |
| outputs\numbers_book\family_360.csv | Product_Family | 4 | 4 | yes | no fan-out |
| outputs\numbers_book\family_360_by_year.csv | year + Product_Family | 16 | 16 | yes | no fan-out |
| outputs\numbers_book\geography.csv | Customer_Governorate + Channel | 39 | 39 | yes | no fan-out |
| outputs\numbers_book\group_operations_360.csv | year + Business_Unit + Primary_KPI | 20 | 20 | yes | no fan-out |
| outputs\numbers_book\line_360.csv | Line_ID | 5 | 5 | yes | no fan-out |
| outputs\numbers_book\location_360.csv | Location_ID | 5 | 5 | yes | no fan-out |
| outputs\numbers_book\location_360_by_year.csv | year + Location_ID | 12 | 12 | yes | no fan-out |
| outputs\numbers_book\machine_360.csv | Machine_ID | 12 | 12 | yes | no fan-out |
| outputs\numbers_book\marketing_360.csv | Platform + campaign_type | 5 | 5 | yes | no fan-out |
| outputs\numbers_book\material_360.csv | Material_ID | 12 | 12 | yes | no fan-out |
| outputs\numbers_book\material_360_by_year.csv | year + Material_ID | 48 | 48 | yes | no fan-out |
| outputs\numbers_book\product_360.csv | Product_ID | 59 | 59 | yes | no fan-out |
| outputs\numbers_book\product_360_by_year.csv | year + Product_ID | 236 | 236 | yes | no fan-out |
| outputs\numbers_book\quality_360.csv | Stage + Defect_Type | 54 | 54 | yes | no fan-out |
| outputs\numbers_book\service_ops_360.csv | month + Channel + Issue_Type + Resolved | 1,383 | 1383 | yes | no fan-out |
| outputs\numbers_book\supplier_360.csv | Supplier_ID | 12 | 12 | yes | no fan-out |
| outputs\numbers_book\supplier_360_by_year.csv | year + Supplier_ID | 48 | 48 | yes | no fan-out |
| outputs\numbers_book\time_360.csv | month | 36 | 36 | yes | no fan-out |
| outputs\numbers_book\totals_and_checks.csv | check_type + name | 24 | 24 | yes | no fan-out |
| outputs\numbers_book\web_360.csv | year + month | 36 | 36 | yes | no fan-out |

## Archived Versioned Tables
- Superseded versioned files (*_vN) were moved from outputs/ and outputs/alerts/ to outputs/archive/ before delivery; they are not part of the delivered set.
- The earlier expanded row counts were caused by pandas categorical groupby calls using unobserved category combinations on categorical fields such as discount_band and cover_band. The current scripts use observed combinations or group without the categorical dimension where it is not part of the grain.
- inventory_location_product_month_v2.csv: archived rows 31,860; current inventory_location_product_month.csv rows 6,372.
- sales_by_year_month_channel_family_product_discount_v1.csv: archived rows 31,765; current sales_by_year_month_channel_family_product_discount.csv rows 17,881.
- sales_discount_relationship_by_channel_v1.csv: archived rows 15; current sales_discount_relationship_by_channel.csv rows 9.

## Current Fan-Out Conclusion
- All current non-versioned tables pass row-count equals distinct-grain-key checks. No current table shows the archived fan-out pattern.
