# ETL using PostgreSQL

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

Since the count matches our dataset, we can safely assume the import was successful.

## Transform
- After getting the dataset, there is a need to clean it. Verify for duplicates as well using **COUNT** function. In this specific dataset, 

<img width="1452" height="203" alt="image" src="https://github.com/user-attachments/assets/a9214f1a-1d0e-4d32-a9ea-c57d7191ee46" />
