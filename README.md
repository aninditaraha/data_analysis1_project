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

## Data Analysis
The dataset includes various features such as order ID, city, ship mode, list price, discount percent, cost price, and order date.  
Unique Ship Modes: `df['Ship Mode'].unique()`

## Technologies Used
- Python
- Pandas
- SQL Server
- Kaggle API

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

# Process data
df.rename(columns={'Order Id': 'order_id', 'City': 'city'}, inplace=True)
df.columns = df.columns.str.lower().str.replace(' ', '_')
df['discount'] = df['list_price'] * df['discount_percent'] * 0.01
df['sale_price'] = df['list_price'] - df['discount']
df['profit'] = df['sale_price'] - df['cost_price']
df['order_date'] = pd.to_datetime(df['order_date'], format="%Y-%m-%d")

# Load the data into SQL Server
import sqlalchemy as sal
engine = sal.create_engine('mssql://LAPTOP-6I8QJQUH\\SQLEXPRESS/master?driver=ODBC+DRIVER+17+FOR+SQL+SERVER')
conn = engine.connect()
df.to_sql('df_orders', con=conn, index=False, if_exists='append')

