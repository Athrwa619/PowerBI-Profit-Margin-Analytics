# PowerBI-Profit-Margin-Analytics
An end-to-end Power BI dashboard analyzing global retail profit margins and identifying revenue leakages.

**Author:** Athrwa Aryan  
**Tech Stack:** Power BI Desktop, Power Query (M), DAX, Data Modeling (Star Schema)

## 📌 Project Overview
An end-to-end business intelligence solution designed to analyze global retail data, identifying critical revenue leakages and optimizing profit margins across distinct product categories and geographic regions.

## ⚙️ Key Features & Technical Implementation
* **ETL Pipeline:** Engineered a robust Power Query script in **M Language** to clean 50,000+ rows of transactional data, handling data-typing anomalies and generating custom calculated columns (e.g., Cost of Goods Sold).
* **Data Modeling:** Normalized flat-file data into a highly efficient **Star Schema**, creating dedicated Fact and Dimension tables (`Fact_Sales`, `Dim_Product`, `Dim_Geography`, `Dim_Date`) to optimize query performance.
* **Advanced DAX:** Developed complex measures for time-intelligence (Year-over-Year margin growth) and dynamic conditional formatting.
* **Interactive UI/UX:** Built a decomposition tree for root-cause analysis and matrix visuals to instantly flag underperforming assets.

## 🧮 Core DAX Logic Showcased
```dax
Profit Margin % = DIVIDE([Total Profit], [Total Revenue], 0)

YoY Margin Growth = 
VAR MarginDiff = [Profit Margin %] - CALCULATE([Profit Margin %], SAMEPERIODLASTYEAR('Date'[Date]))
RETURN DIVIDE(MarginDiff, CALCULATE([Profit Margin %], SAMEPERIODLASTYEAR('Date'[Date])), 0)
