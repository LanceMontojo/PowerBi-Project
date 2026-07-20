# Overview

This is an independent project I put together to sharpen my data analysis skills using Power BI and PostgreSQL. Because finding a clean dataset in the real world is rare, I’m using the [Retail Store Sales: Dirty for Data Cleaning](https://www.kaggle.com/datasets/ahmedmohamed2003/retail-store-sales-dirty-for-data-cleaning). This gives me a great opportunity to dive deep into the full ETL (Extract, Load, Transform) process and tackle messy, real-world data cleaning challenges before building out the dashboards.

## PostgreSQL
The first phase of the project focused on performing a complete ETL pipeline using PostgreSQL. Starting from the raw dataset, the following preprocessing steps were performed:

- Imported the raw dataset into PostgreSQL.
- Handled missing values using appropriate imputation and validation techniques.
- Removed duplicate records.
- Validated feature relationships and data consistency.
- Detected and evaluated potential outliers using the IQR method.
- Standardized data types and prepared the dataset for analysis.
- Exported a clean master dataset.

Throughout the process, every preprocessing decision was documented to ensure the final dataset maintained both data quality and integrity.

## Power BI
Instead of importing the cleaned PostgreSQL dataset, I repeated the entire ETL pipeline using the original raw dataset in **Power Query**. This allowed me to reinforce the same preprocessing concepts while becoming familiar with Power BI's transformation capabilities.

The Power Query workflow included:

- Importing the raw dataset.
- Handling missing values.
- Removing duplicate records.
- Validating feature relationships.
- Detecting and evaluating outliers.
- Applying appropriate data types.
- Loading the cleaned dataset into the Power BI data model.

After completing the ETL process, an interactive dashboard was developed to explore:

- Revenue trends over time.
- Category performance.
- Seasonal purchasing behavior.
- Payment method preferences.
- Online vs. In-store sales.
- Customer purchasing patterns.

# Key Findings

Overall, the analysis suggests that **Butchers** should remain a priority for inventory management and promotional efforts, as it consistently generated the highest total revenue despite showing a gradual decline over the years. At the same time, the steady growth of **Beverages**, **Computers and Electric Accessories**, and **Furniture** indicates increasing customer demand, making these categories strong candidates for continued investment and targeted promotions.

Although **Milk Products** contributed the least revenue overall, sales consistently increased during **December** and **January**. Retailers may consider increasing inventory levels during this period while avoiding unnecessary overstock throughout the rest of the year to better match seasonal demand.

In terms of customer purchasing behavior, **Cash** remained the most preferred payment method, highlighting the importance of maintaining efficient cash handling and checkout operations. Additionally, **Online** sales slightly outperformed **In-store** purchases, suggesting that continued investment in online services and digital customer engagement could further support future revenue growth.

By completing the entire workflow in both **PostgreSQL** and **Power BI**, I gained hands-on experience in data cleaning, transformation, validation, and visualization, reinforcing how reliable data preparation serves as the foundation for producing meaningful insights and supporting data-driven business decisions.
