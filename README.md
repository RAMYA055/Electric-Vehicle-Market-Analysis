Power BI | DAX | SQL | Excel
Power BI SQL Excel Python

📌 Project Overview
A full-stack data analytics project analyzing 150,000+ electric vehicle transactions across 15 US states from 2019–2024. Built to surface high-growth markets, track adoption trends, and model revenue potential — delivered as an interactive Power BI dashboard backed by a robust SQL and DAX layer.

Resume Bullets:

Built Power BI dashboard analyzing 150K+ EV transaction records to identify high-growth regions and BEV adoption trends using star schema modeling
Designed 19 complex DAX measures including YoY revenue growth, rolling averages, and a proprietary Revenue Potential Scoring model
Authored 15+ SQL queries (CTEs, window functions, RANK, LAG) for regional performance, cohort analysis, and incentive impact measurement
📊 Key Metrics at a Glance
Metric	Value
📁 Total Records	150,000 transactions
💰 Total Revenue	~$8.9 Billion
🗓️ Time Period	2019 – 2024
🗺️ Geography	15 US States
🚗 Brands Covered	12 major EV brands
🔋 Vehicle Types	BEV, PHEV, HEV
👤 Customer Segments	Individual, Fleet, Commercial, Government
⚡ BEV Market Share	~55% of transactions
💚 Incentive Rate	~58% of buyers used federal credits
🗂️ Repository Structure
ev-market-analysis/
│
├── 📄 README.md                          # This file
│
├── 📊 EV_Market_Analysis_Dashboard.xlsx  # 7-tab Excel workbook
│   ├── Sheet 1: Executive Dashboard
│   ├── Sheet 2: Regional Analysis
│   ├── Sheet 3: Brand & Model Analysis
│   ├── Sheet 4: DAX Measures (Power BI)
│   ├── Sheet 5: SQL Queries Reference
│   ├── Sheet 6: Market Insights
│   └── Sheet 7: Data Sample (5K rows)
│
├── 📋 EV_Market_Data_150k.csv            # Full 150K-row dataset (19 fields)
│
├── 🗄️ EV_Market_SQL_Queries.sql          # 15 analytical SQL queries + schema
│
└── 📘 EV_Market_PowerBI_Guide.docx       # Power BI setup & DAX reference guide
🛠️ Tech Stack
Tool	Usage
Power BI Desktop	Interactive dashboard, star schema modeling, slicers
DAX	19 measures: KPIs, time intelligence, market share, scoring
SQL (MySQL / PostgreSQL)	Schema design, 15 analytical queries, views
Excel (openpyxl)	7-tab workbook with conditional formatting and charts
Python (pandas, numpy)	Dataset generation, data transformation
📐 Data Model (Star Schema)
                    ┌─────────────┐
                    │  dim_date   │
                    │─────────────│
                    │ date_key PK │
                    │ year        │
                    │ quarter     │
                    │ month_name  │
                    │ season      │
                    └──────┬──────┘
                           │
┌─────────────┐    ┌───────▼────────┐    ┌──────────────┐
│ dim_region  │    │   ev_sales     │    │  (Brand Dim) │
│─────────────│    │   (FACT TABLE) │    │──────────────│
│ region_id PK│◄───│ transaction_id │    │  brand       │
│ region_name │    │ sale_date  FK  │    │  vehicle_type│
│ state_code  │    │ region     FK  │    │  model       │
│ census_reg  │    │ brand          │    └──────────────┘
│ timezone    │    │ sale_price_usd │
└─────────────┘    │ vehicle_type   │
                   │ satisfaction   │
                   │ incentive_flag │
                   │ dealer_revenue │
                   └────────────────┘
📈 DAX Measures Implemented
Core KPI Measures (click to expand)
Time Intelligence (click to expand)
Market Share & Scoring (click to expand)
🗄️ SQL Highlights
Regional Revenue Potential Scoring (click to expand)
YoY Growth with Window Functions (click to expand)
Full query list (15 total):

#	Query	Technique Used
Q01	Executive KPI Summary	UNION ALL aggregations
Q02	Regional Market Analysis	GROUP BY + window functions
Q03	YoY Growth Analysis	LAG(), cumulative SUM() OVER
Q04	Brand Competitive Analysis	RANK(), DENSE_RANK()
Q05	Revenue Potential Scoring	CTE + weighted composite formula
Q06	Vehicle Type Trends	PARTITION BY year, quarter
Q07	Customer Segment Deep Dive	FILTER + segment share
Q08	Rolling 3-Month Revenue	ROWS BETWEEN window frame
Q09	Price Tier Segmentation	CASE WHEN classification
Q10	Incentive Impact Analysis	Conditional aggregation
Q11	Top Models by Region	RANK() PARTITION BY region
Q12	Satisfaction Drivers	Multi-group correlation
Q13	Dealer Performance	Effective margin calculation
Q14	Market Share Trends	Share % OVER year partition
Q15	Fleet vs Individual Buyers	Cohort YoY with LAG()
📊 Dashboard Pages (Power BI)
Page	Visuals	Key Insight
Executive Overview	7 KPI cards, line chart, donut	Revenue trends, BEV share
Regional Analysis	Map, bar chart, matrix	California leads; TX/FL growth opportunity
Brand Competitiveness	Scatter, bar, table	Tesla dominates; Rivian premium niche
Adoption Trends	Line, area, waterfall	BEV accelerating post-2021
Customer Segments	Stacked bar, matrix	Fleet buyers = higher avg spend
Incentive Analysis	Gauge, comparison bars	58% incentive rate; $7,500 avg credit
🔑 Key Findings
🏆 California dominates with the highest revenue share among all regions (~22% of total)
📈 BEV acceleration — pure electric vehicles grew from 45% to 60%+ of sales by 2024
💰 Incentive impact — buyers using federal credits show higher satisfaction and larger vehicle purchases
🎯 Texas & Florida have high volume but lower BEV penetration — prime markets for infrastructure investment
🚀 Tesla leads with ~28% unit market share and highest brand revenue across all years
👥 Fleet segment averages 12–15% higher transaction values than individual buyers
🔌 DC Fast Charging adoption correlates with higher satisfaction scores in BEV segment
🚀 How to Use
Option 1: Power BI Dashboard
Download EV_Market_Data_150k.csv
Open Power BI Desktop → Get Data → Text/CSV
Build star schema with dim_date and dim_region
Mark dim_date as a Date Table
Copy DAX measures from Sheet 4 of the Excel workbook
Refer to EV_Market_PowerBI_Guide.docx for full setup instructions
Option 2: SQL Analysis
# MySQL
mysql -u root -p < EV_Market_SQL_Queries.sql

# PostgreSQL
psql -U postgres -f EV_Market_SQL_Queries.sql

# Then import CSV
LOAD DATA INFILE 'EV_Market_Data_150k.csv'
INTO TABLE ev_sales FIELDS TERMINATED BY ',' IGNORE 1 ROWS;
Option 3: Excel Workbook
Open EV_Market_Analysis_Dashboard.xlsx directly — all 7 tabs are pre-built with data, formulas, and conditional formatting.

📋 Dataset Fields
Field	Type	Description
transaction_id	VARCHAR	Unique record ID (EV0000001 format)
sale_date	DATE	Transaction date
year / quarter / month	INT	Time partitioning fields
region	VARCHAR	US state of sale
brand	VARCHAR	Vehicle manufacturer
model	VARCHAR	Specific model name
vehicle_type	VARCHAR	BEV / PHEV / HEV
sale_price_usd	DECIMAL	Gross sale price
electric_range_miles	INT	EPA-rated range
charging_type	VARCHAR	DC Fast / Level 2 / Both
customer_segment	VARCHAR	Individual / Fleet / Commercial / Gov
incentive_applied	BOOLEAN	Federal credit used flag
federal_tax_credit	DECIMAL	Credit amount ($0, $3,750, or $7,500)
net_price_usd	DECIMAL	Price after tax credit
satisfaction_score	DECIMAL	Customer rating (1.0–5.0)
dealer_margin_pct	DECIMAL	Dealer gross margin percentage
dealer_revenue_usd	DECIMAL	Dealer profit per transaction
🏗️ Project Setup (Reproduce Dataset)
# Clone the repo
git clone https://github.com/yourusername/ev-market-analysis.git
cd ev-market-analysis

# Install Python dependencies
pip install pandas numpy openpyxl

# Regenerate the 150K dataset (if needed)
python generate_dataset.py

# Rebuild the Excel workbook
python create_excel.py
Requirements:

Python 3.8+
pandas, numpy, openpyxl
Power BI Desktop (free) for dashboard
MySQL 8+ or PostgreSQL 14+ for SQL queries
📁 Files for Google Drive Upload
Create a folder named EV_Market_Analysis_Project and upload all 4 files:

EV_Market_Analysis_Project/
├── EV_Market_Data_150k.csv              ← Import into Power BI / SQL
├── EV_Market_Analysis_Dashboard.xlsx   ← Open directly in Excel
├── EV_Market_SQL_Queries.sql            ← Run in any SQL client
└── EV_Market_PowerBI_Guide.docx        ← Follow for Power BI setup
👤 Author
Built as a portfolio data analytics project demonstrating end-to-end skills in:

Data Engineering — schema design, dataset generation, SQL views
Business Intelligence — Power BI modeling, DAX time intelligence
Analytics — market segmentation, cohort analysis, scoring models
Visualization — executive dashboards, conditional formatting, KPI design
📄 License
This project is for portfolio and educational purposes. Dataset is synthetically generated.
