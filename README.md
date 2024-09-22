<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Retail Orders Analysis</title>
</head>
<body>
    <h1>Retail Orders Analysis Project</h1>

    <h2>Project Overview</h2>
    <p>This project involves analyzing retail order data to derive insights into sales performance, discounts, and profits. The analysis is conducted using Python, pandas, and SQL Server.</p>

    <h2>Project Structure</h2>
    <ul>
        <li><strong>Data Acquisition</strong>
            <ul>
                <li>Downloaded retail order data from Kaggle.</li>
            </ul>
        </li>
        <li><strong>Data Preparation</strong>
            <ul>
                <li>Handled null values by specifying na_values during data loading.</li>
                <li>Renamed columns for consistency and clarity.</li>
                <li>Derived new columns: <em>discount</em>, <em>sale_price</em>, and <em>profit</em>.</li>
            </ul>
        </li>
        <li><strong>Data Processing</strong>
            <ul>
                <li>Converted <em>order_date</em> from object data type to datetime format.</li>
            </ul>
        </li>
        <li><strong>Data Loading</strong>
            <ul>
                <li>Connected to SQL Server and loaded the processed data into the database.</li>
            </ul>
        </li>
    </ul>

    <h2>Code Snippet</h2>
    <pre>
        <code>
            import kaggle
            # Download the file
            !kaggle datasets download ankitbansal06/retail-orders -f orders.csv
            import zipfile
            zip_ref = zipfile.ZipFile('orders.csv.zip') 
            zip_ref.extractall()
            import pandas as pd
            df = pd.read_csv('orders.csv', na_values=['Not Available', 'unknown'])
            # Process data...
        </code>
    </pre>

    <h2>Data Analysis</h2>
    <p>The dataset includes various features such as order ID, city, ship mode, list price, discount percent, cost price, and order date.</p>
    <p>Unique Ship Modes: <code>df['Ship Mode'].unique()</code></p>

    <h2>Technologies Used</h2>
    <ul>
        <li>Python</li>
        <li>Pandas</li>
        <li>SQL Server</li>
        <li>Kaggle API</li>
    </ul>

    <h2>License</h2>
    <p>This project is licensed under the MIT License.</p>

    <h2>Contact</h2>
    <p>For inquiries, please contact me at <a href="mailto:aninditaraha902@gmail.com">aninditaraha902@gmail.com</a>.</p>
</body>
</html>

