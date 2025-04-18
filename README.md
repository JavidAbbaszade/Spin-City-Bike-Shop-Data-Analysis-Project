# Spin City Bike Shop – Data Analysis Project

## Project Overview
This project analyzes sales and cost data from Spin City Bike Shop over two years (2021 and 2022). The goal is to evaluate business performance, uncover trends, and provide data-driven pricing recommendations.

## Technologies Used
- Microsoft SQL Server  
- Power BI  
- Excel  

## Datasets
The project uses three CSV files:
- `bike_share_yr_0.csv`: Sales data from 2021  
- `bike_share_yr_1.csv`: Sales data from 2022  
- `cost_table.csv`: Cost of goods sold (COGS) per year  

## SQL Query
Data was processed using the following SQL query:

```sql
WITH cte AS (
    SELECT * FROM bike_share_yr_0
    UNION ALL
    SELECT * FROM bike_share_yr_1
)
SELECT 
    dteday,
    season,
    a.yr,
    weekday,
    hr,
    rider_type,
    riders,
    price,
    COGS,
    riders * price AS revenue,
    riders * price - COGS * riders AS profit
FROM cte a
LEFT JOIN cost_table b
ON a.yr = b.yr;
```
## Power BI Dashboard
Visualizations were created in Power BI to highlight trends and insights.

**2021 Dashboard:**


**2022 Dashboard:**


## Analysis and Insights
**Revenue Growth:** Revenue increased significantly in 2022 compared to 2021, driven by more riders and higher prices.

**Profit Margins:** Profit margins also improved. However, caution is advised with further price increases to avoid reduced customer demand.

**Seasonality:** Revenue and profit vary significantly by season, with peaks during warmer months.

## Recommendations
Consider a 10–15% price increase to test market response.

Use segmented pricing strategies for casual vs. registered riders.

Monitor customer behavior and adjust pricing as needed.

Conduct additional market research to support long-term strategy.

## How to Run the Project
Download the dataset files: bike_share_yr_0.csv, bike_share_yr_1.csv, and cost_table.csv.

Import them into a SQL database (e.g., SQL Server).

Run the provided SQL query to generate revenue and profit metrics.

Load the output into Power BI and build dashboards.
