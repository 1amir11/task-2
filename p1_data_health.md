# Phase 1 Data Health

Except Product_Master.csv, Business_Units.csv and Locations.csv, the dataset is modeled/synthetic training data anchored to public products/prices; findings are decision-dashboard evidence, not audited company facts.

## Files and Grain Checks

### Business_Units.csv

- Dictionary grain: 1 row per company business unit

- Data class: public/verified

- Rows: 5; Columns: 5

- Key check Business_Unit: 5 distinct / 5 rows; unique=True; duplicates=0



### Case_Briefs.csv

- Dictionary grain: not listed

- Data class: modeled

- Rows: 10; Columns: 4



### Customer_Service.csv

- Dictionary grain: 1 row per support ticket

- Data class: modeled

- Rows: 6,500; Columns: 9

- Key check Ticket_ID: 6,500 distinct / 6,500 rows; unique=True; duplicates=0

- Date Open_Date: 2023-10-01 to 2026-09-30; 36 distinct months; month gaps=0



### Customers.csv

- Dictionary grain: 1 row per anonymized customer ID

- Data class: modeled

- Rows: 30,000; Columns: 9

- Key check Customer_ID: 30,000 distinct / 30,000 rows; unique=True; duplicates=0

- Date Join_Date: 2023-10-01 to 2026-09-30; 36 distinct months; month gaps=0



### Data_Dictionary.csv

- Dictionary grain: not listed

- Data class: modeled

- Rows: 19; Columns: 4



### Group_Operations.csv

- Dictionary grain: month x business unit

- Data class: modeled

- Rows: 180; Columns: 7

- Key check Month: 36 distinct / 180 rows; unique=False; duplicates=144

- Key check Business_Unit: 5 distinct / 180 rows; unique=False; duplicates=175

- Key check Month + Business_Unit: 180 distinct / 180 rows; unique=True; duplicates=0

- Date Month: 2023-10-01 to 2026-09-01; 36 distinct months; month gaps=0

- Percent/rate scale scan: Operational_Efficiency_Pct min=73.5 max=98



### Inventory_History.csv

- Dictionary grain: month x location x product

- Data class: modeled

- Rows: 6,372; Columns: 19

- Key check Snapshot_Month: 36 distinct / 6,372 rows; unique=False; duplicates=6,336

- Key check Location_ID: 3 distinct / 6,372 rows; unique=False; duplicates=6,369

- Key check Product_ID: 59 distinct / 6,372 rows; unique=False; duplicates=6,313

- Key check Snapshot_Month + Location_ID + Product_ID: 6,372 distinct / 6,372 rows; unique=True; duplicates=0

- Date Snapshot_Month: 2023-10-01 to 2026-09-01; 36 distinct months; month gaps=0



### Locations.csv

- Dictionary grain: 1 row per channel / operating location

- Data class: public/verified

- Rows: 5; Columns: 9

- Key check Location_ID: 5 distinct / 5 rows; unique=True; duplicates=0



### Machine_Downtime.csv

- Dictionary grain: 1 row per downtime event

- Data class: modeled

- Rows: 2,800; Columns: 8

- Key check Downtime_ID: 2,800 distinct / 2,800 rows; unique=True; duplicates=0

- Date Date: 2023-10-02 to 2026-09-30; 36 distinct months; month gaps=0



### Marketing.csv

- Dictionary grain: 1 row per campaign

- Data class: modeled

- Rows: 420; Columns: 15

- Key check Campaign_ID: 420 distinct / 420 rows; unique=True; duplicates=0

- Date Start_Date: 2023-10-08 to 2026-09-18; 36 distinct months; month gaps=0

- Date End_Date: 2023-10-22 to 2026-09-30; 36 distinct months; month gaps=0

- Percent/rate scale scan: Discount_Pct min=0 max=0.25



### Materials.csv

- Dictionary grain: 1 row per material

- Data class: modeled

- Rows: 12; Columns: 6

- Key check Material_ID: 12 distinct / 12 rows; unique=True; duplicates=0



### Printing_Batches.csv

- Dictionary grain: 1 row per print batch

- Data class: modeled

- Rows: 1,900; Columns: 15

- Key check Print_Batch_ID: 1,900 distinct / 1,900 rows; unique=True; duplicates=0

- Date Print_Date: 2023-10-01 to 2026-09-30; 36 distinct months; month gaps=0



### Product_BOM.csv

- Dictionary grain: product x material

- Data class: modeled

- Rows: 337; Columns: 7

- Key check Product_ID: 59 distinct / 337 rows; unique=False; duplicates=278

- Key check Material_ID: 10 distinct / 337 rows; unique=False; duplicates=327

- Key check Product_ID + Material_ID: 337 distinct / 337 rows; unique=True; duplicates=0



### Product_Master.csv

- Dictionary grain: 1 row per public product

- Data class: public/verified

- Rows: 59; Columns: 12

- Key check Product_ID: 59 distinct / 59 rows; unique=True; duplicates=0

- Key check SKU: 59 distinct / 59 rows; unique=True; duplicates=0

- Key check Product_ID + SKU: 59 distinct / 59 rows; unique=True; duplicates=0



### Production_Orders.csv

- Dictionary grain: 1 row per production order

- Data class: modeled

- Rows: 2,500; Columns: 16

- Key check Production_Order_ID: 2,500 distinct / 2,500 rows; unique=True; duplicates=0

- Date Start_Date: 2023-10-01 to 2026-09-10; 36 distinct months; month gaps=0

- Date Due_Date: 2023-10-09 to 2026-10-01; 37 distinct months; month gaps=0

- Date Completion_Date: 2023-10-09 to 2026-09-30; 36 distinct months; month gaps=0

- High-null columns: Primary_Bottleneck (83.72%)

- Percent/rate scale scan: Efficiency_Pct min=48.3 max=97



### Purchase_Orders.csv

- Dictionary grain: 1 row per material PO

- Data class: modeled

- Rows: 3,600; Columns: 13

- Key check PO_ID: 3,600 distinct / 3,600 rows; unique=True; duplicates=0

- Date Order_Date: 2023-10-01 to 2026-09-15; 36 distinct months; month gaps=0

- Date Promised_Date: 2023-10-08 to 2026-10-06; 37 distinct months; month gaps=0

- Date Actual_Receipt_Date: 2023-10-08 to 2026-09-30; 36 distinct months; month gaps=0



### Quality.csv

- Dictionary grain: 1 row per QC inspection

- Data class: modeled

- Rows: 9,000; Columns: 12

- Key check QC_ID: 9,000 distinct / 9,000 rows; unique=True; duplicates=0

- Date Inspection_Date: 2023-10-01 to 2026-09-30; 36 distinct months; month gaps=0



### Sales_Transactions.csv

- Dictionary grain: 1 row per invoice line

- Data class: modeled

- Rows: 180,000; Columns: 30

- Key check Row_ID: 180,000 distinct / 180,000 rows; unique=True; duplicates=0

- Key check Invoice_ID: 180,000 distinct / 180,000 rows; unique=True; duplicates=0

- Key check Row_ID + Invoice_ID: 180,000 distinct / 180,000 rows; unique=True; duplicates=0

- Date Order_Date: 2023-10-01 to 2026-09-30; 36 distinct months; month gaps=0

- Date Month_Key: 2023-10-01 to 2026-09-01; 36 distinct months; month gaps=0

- Date Return_Date: 2023-10-04 to 2026-09-30; 36 distinct months; month gaps=0

- High-null columns: Return_Date (95.25%)

- Percent/rate scale scan: Discount_Pct min=0 max=0.38; Gross_Margin_Pct min=-0.1417 max=0.51



### Suppliers.csv

- Dictionary grain: 1 row per anonymized supplier

- Data class: modeled

- Rows: 12; Columns: 7

- Key check Supplier_ID: 12 distinct / 12 rows; unique=True; duplicates=0



### Web_Traffic_Daily.csv

- Dictionary grain: 1 row per day

- Data class: modeled

- Rows: 1,096; Columns: 11

- Key check Date: 1,096 distinct / 1,096 rows; unique=True; duplicates=0

- Date Date: 2023-10-01 to 2026-09-30; 36 distinct months; month gaps=0

- Percent/rate scale scan: New_User_Pct min=0.51 max=0.72; Mobile_Pct min=0.72 max=0.88; Add_To_Cart_Rate min=0.04 max=0.18; Checkout_Rate min=0.02 max=0.0869; Conversion_Rate min=0.0114 max=0.0481



## Foreign Key Orphan Checks

- Inventory_History.csv.Product_ID -> Product_Master.csv: 0 orphan distinct of 59 values; examples=[]

- Inventory_History.csv.Location_ID -> Locations.csv: 0 orphan distinct of 3 values; examples=[]

- Marketing.csv.Product_ID -> Product_Master.csv: 0 orphan distinct of 58 values; examples=[]

- Printing_Batches.csv.Product_ID -> Product_Master.csv: 0 orphan distinct of 59 values; examples=[]

- Product_BOM.csv.Product_ID -> Product_Master.csv: 0 orphan distinct of 59 values; examples=[]

- Product_BOM.csv.Material_ID -> Materials.csv: 0 orphan distinct of 10 values; examples=[]

- Production_Orders.csv.Product_ID -> Product_Master.csv: 0 orphan distinct of 59 values; examples=[]

- Purchase_Orders.csv.Supplier_ID -> Suppliers.csv: 0 orphan distinct of 12 values; examples=[]

- Purchase_Orders.csv.Material_ID -> Materials.csv: 0 orphan distinct of 12 values; examples=[]

- Quality.csv.Product_ID -> Product_Master.csv: 0 orphan distinct of 59 values; examples=[]

- Sales_Transactions.csv.Product_ID -> Product_Master.csv: 0 orphan distinct of 59 values; examples=[]

- Sales_Transactions.csv.Customer_ID -> Customers.csv: 0 orphan distinct of 25634 values; examples=[]

- Sales_Transactions.csv.Location_ID -> Locations.csv: 0 orphan distinct of 3 values; examples=[]


## Derived Column Recomputations

- sales Gross_Sales_EGP = Quantity * List_Price_EGP: checked 180,000; mismatches 0; max abs diff 0.0

- sales Net_Sales_EGP = Gross_Sales_EGP * (1 - Discount_Pct): checked 180,000; mismatches 0; max abs diff 0.0

- sales Gross_Profit_EGP = Net_Sales_EGP - Estimated_COGS_EGP: checked 180,000; mismatches 0; max abs diff 0.0

- sales Gross_Margin_Pct = Gross_Profit_EGP / Net_Sales_EGP: checked 180,000; mismatches 0; max abs diff 0.0

- inventory Closing_Stock = Opening + Received - Sold + Returned - Damaged: checked 6,372; mismatches 147; max abs diff 2108.0

- inventory Days_of_Cover = Closing_Stock / Avg_Daily_Sales_90D: checked 6,372; mismatches 0; max abs diff 0.05

- purchase accepted + rejected = ordered: checked 3,600; mismatches 0; max abs diff 0.0

- production Good_Qty + Rejected_Qty = Produced_Qty: checked 2,500; mismatches 0; max abs diff 0.0

- production Delay_Days = max(Completion_Date - Due_Date, 0): checked 2,500; mismatches 0; max abs diff 0.0

- printing Good_Qty + Rejected_Qty = Printed_Qty: checked 1,900; mismatches 0; max abs diff 0.0

- quality Passed_Qty + Rejected_Qty = Inspected_Qty: checked 9,000; mismatches 0; max abs diff 0.0

- web Conversion_Rate = Orders / Sessions: checked 1,096; mismatches 9; max abs diff 0.0013


## Ranked Data Problems

1. Severity 3 | affects Inventory | derived-column: inventory Closing_Stock = Opening + Received - Sold + Returned - Damaged has 147 mismatches.

2. Severity 3 | affects Marketing/Web | derived-column: web Conversion_Rate = Orders / Sessions has 9 mismatches.

3. Severity 3 | affects Understand | Case_Briefs.csv: File is not listed in Data_Dictionary.csv.

4. Severity 3 | affects Understand | Data_Dictionary.csv: File is not listed in Data_Dictionary.csv.

5. Severity 3 | affects Understand | Sources.csv: Dictionary entry without file; confirm whether Sources.csv should be supplied or removed from Data_Dictionary.csv.

6. Severity 2 | affects All | Production_Orders.csv: High-null columns may be subset-only fields: Primary_Bottleneck (83.72%).

7. Severity 2 | affects All | Sales_Transactions.csv: High-null columns may be subset-only fields: Return_Date (95.25%).


## 10-Line Phase Summary

- 1. Ran scripts/p1_inventory.py over 20 raw CSV files.

- 2. Data_Dictionary.csv was read first and used as the declared grain source.

- 3. Product_Master.csv, Business_Units.csv and Locations.csv are the only public/verified tables.

- 4. All other operational tables are treated as modeled/synthetic training data.

- 5. Key uniqueness was checked from declared ID-like columns and grain hints.

- 6. Date ranges and month gaps were profiled from every date/month-like column.

- 7. Product, customer, location, supplier and material foreign keys were checked for orphans.

- 8. Stored money, margin, inventory balance, delay, yield and conversion fields were recomputed from components.

- 9. High-null subset fields were flagged rather than dropped.

- 10. Ranked data problems written to outputs/p1_data_health.md.
