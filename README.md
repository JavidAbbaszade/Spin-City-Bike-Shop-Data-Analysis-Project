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
![img](https://raw.githubusercontent.com/JavidAbbaszade/Spin-City-Bike-Shop-Data-Analysis-Project/refs/heads/main/2021.JPG)

**2022 Dashboard:**
![img](https://raw.githubusercontent.com/JavidAbbaszade/Spin-City-Bike-Shop-Data-Analysis-Project/refs/heads/main/2022.JPG)

# Data Analysis: Pricing Strategy Recommendation

This repository provides a detailed analysis and recommendation for adjusting the pricing strategy based on last year's price increase and market behavior. The goal is to determine a conservative pricing increase that optimizes revenue without losing customers.

## Problem Overview

Given the substantial price increase last year, we need to assess the potential impact of a more conservative price increase. This analysis aims to test the market's response to a 10-15% price adjustment and how different strategies might affect demand.

## Pricing Increase Strategy

### Conservative Price Increase:
- A more conservative price increase is suggested to prevent demand from dropping due to price sensitivity.
- **Recommended Increase**: A 10-15% increase on the current price of $4.99.

### Price Projections:
- **10% Increase**:  
  New Price: $5.49  
  Formula: `4.99 * (1 + 0.10)`
  
- **15% Increase**:  
  New Price: $5.74  
  Formula: `4.99 * (1 + 0.15)`

## Recommended Strategy

### 1. Market Analysis:
- **Objective**: Conduct further market research to understand customer satisfaction, potential competitive changes, and the economic environment.
- **Outcome**: This will help guide whether to lean towards the lower or higher end of the price increase range.

### 2. Segmented Pricing Strategy:
- **Strategy**: Consider applying different pricing for casual users vs. registered users.
  - Registered users may have lower price sensitivity and could be charged higher.
  - Casual users may be more sensitive to price changes and could benefit from a lower price increase.

### 3. Monitor and Adjust:
- **Implementation**: After applying the new prices, it is essential to monitor customer feedback and sales data closely.
- **Outcome**: This will help fine-tune the pricing strategy and allow for adjustments if the new price turns out to be too high or low.

## Conclusion

This recommendation proposes a gradual and conservative price increase strategy while ensuring close monitoring and adaptability to customer response. This approach balances revenue optimization with customer retention, leveraging market research and segmented pricing to tailor the price changes effectively.

## Next Steps

1. Conduct market research to validate assumptions about customer behavior and competitive changes.
2. Implement the new pricing structure.
3. Monitor the response and sales data to adjust as needed.


## How to Run the Project
Download the dataset files: bike_share_yr_0.csv, bike_share_yr_1.csv, and cost_table.csv.

Import them into a SQL database (e.g., SQL Server).

Run the provided SQL query to generate revenue and profit metrics.

Load the output into Power BI and build dashboards.
