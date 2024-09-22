# Retail Orders Analysis Project

## Project Overview
This project involves analyzing retail order data to derive insights into sales performance, discounts, and profits. The analysis is conducted using Python, pandas, and SQL Server.

## Project Structure
- **Data Acquisition**
  - Downloaded retail order data from Kaggle.
- **Data Preparation**
  - Handled null values by specifying `na_values` during data loading.
  - Renamed columns for consistency and clarity.
  - Derived new columns: *discount*, *sale_price*, and *profit*.
- **Data Processing**
  - Converted *order_date* from object data type to datetime format.
- **Data Loading**
  - Connected to SQL Server and loaded the processed data into the database.

## Code Snippet
```python
import kaggle
# Download the file
!kaggle datasets download ankitbansal06/retail-orders -f orders.csv
import zipfile
zip_ref = zipfile.ZipFile('orders.csv.zip') 
zip_ref.extractall()
import pandas as pd
df = pd.read_csv('orders.csv', na_values=['Not Available', 'unknown'])
# Process data...


