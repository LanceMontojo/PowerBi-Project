# ETL with PostgreSQL

Because this dataset is intentionally messy, I wanted to document my exact thought process and the steps I took to clean it. 
This section outlines my systematic approach to handling the "dirty" work, including managing missing values and removing duplicates and more
using PostgreSQL.

## Extract
The dataset is provided in a Comma-Separated Values (CSV) file, making it straightforward to import into PostgreSQL. 
The extraction process consisted of the following steps:
- Create a database named retail_sales_raw, as the dataset is still in its raw form and has not yet undergone preprocessing. 

- Create a table within the database, either by manually defining the columns or by using SQL commands such as **CREATE TABLE**.
Initially assign all columns with **TEXT** data type to all columns. Doing it this way ensures that PostgreSQL 
imports the data exactly as it appears in the CSV file and prevents import failures caused by datatype mismatches, invalid values, or missing data.

- Verify that the import was successful by using **COUNT** function to check whether the number of rows in the table matches the number of 
records in the original dataset.

<p align = "center">
  <img width="167" height="82" alt="image" src="https://github.com/user-attachments/assets/c07a977e-96c3-4814-819a-eb0b68f1ed1c" />
</p>

Since the count matches our dataset, we can safely assume the import was successful. The first five datapoint of our dataset looks like:

<img width="1452" height="203" alt="image" src="https://github.com/user-attachments/assets/a9214f1a-1d0e-4d32-a9ea-c57d7191ee46" />

## Transform
- After obtaining the dataset, the first step should be assessing the data quality by checking for duplicates. By using the **COUNT** function, duplicate valeus can be identified and investigated. In this specific dataset, Transaction_ID seems to be the unique identifier, so it is useful to know if there are duplicated values of data points in that column. The reasoning I have for this is that

  - Customer_ID may contain duplicate values because a customer can make multiple purchases over time.
  - Transaction_Date may contain duplicate values because many transactions can occur on the same day
  - Category contains a fixed set of product categories that are shared across many transactions.
  - Item cannot be a unique identifier either because the same item can be purchased by different customers and across multiple transactions. For example,       Item_10_PAT belongs to the Patisserie category and can appear in many records.
  - Price_Per_Unit is not unique because multiple transactions may involve the same item at the same price.
  - Quantity is simply the number of units purchased and can naturally repeat across transactions.
  - Payment_Method, Location, and Discount_Applied are descriptive attributes and are expected to have many repeated values.

 - Based on this reasoning, Transaction_ID is the most appropriate column to check for duplicate records. If duplicate Transaction_IDs are found, they may indicate duplicate transaction entries in the dataset.

<p align = "Center">
  <img width="738" height="157" alt="image" src="https://github.com/user-attachments/assets/9294b178-2cd3-49af-b18f-89a7f3ad60bd" />
</p>

This verifies that there are no duplicate values and therefore we can move to the next step.

- For the next step of data assessment, we check for missing values across all features in the dataset.
<img width="1457" height="95" alt="image" src="https://github.com/user-attachments/assets/bdf1b4a7-9d2a-44cc-b950-ad210165e282" />

<p align = "center">
  <img width="570" height="87" alt="image" src="https://github.com/user-attachments/assets/39f6bf24-0b96-4130-8d59-7e5ea64de14a" />
</p>

<p align = "center">
  <img width="670" height="281" alt="image" src="https://github.com/user-attachments/assets/51b0c6ab-10c5-407e-b809-217d95dcbc62" />
</p>

As shown in the results, the features Item, Price_Per_Unit, Quantity, Total_Spent, and Discount_Applied contain missing values. Since these fields are important for understanding transaction details and sales performance, further investigation is required before deciding how to handle the missing data.
