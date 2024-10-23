# Home_Sales

This script sets up a PySpark environment in Google Colab, reads data from an AWS S3 bucket, and performs SQL based operations using SparkSQL.

Environment Setup:
Java 8 and Apache Spark, findspark are installed to integrate PySpark with Google Colab. Sets environment variables for Java and Spark and initializes findspark to set up the Spark environment. Finally, the Spark session is created and the Google Drive is mounted.

Data Loading:
A CSV file is read in from an AWS S3 bucket into a Spark DataFrame (df_sales). A temp view (home_sales) is created to run SQL queries on the DataFrame.

SQL Queries:
SparkSQL is used to calculate the average prices for the following questions:
Query 1: Calculates the average price for four-bedroom homes sold per year, rounded to two decimal places, and shows the result.
Query 2: Calculates the average price of homes (with 3 bedrooms and 3 bathrooms) per year built, rounding to two decimal places.
Query 3: Calculates the average price of homes (with 3 bedrooms, 3 bathrooms, 2 floors, and at least 2,000 sq. ft.) per year built, rounding to two decimal places.
Query 4: Calculates the average price per "view" rating, rounding to two decimal places, for homes with an average price greater than $350,000. The runtime is measured for this query.

Caching:
The home_sales temp table is cached to memory to optimize performance. Cached data is run for the same query (average price per view rating) and runtime is compared to the uncached version.

Parquet Data Operations:
DataFrame is partitioned by the date_built field and writes it in Parquet format then reads the Parquet data back into a DataFrame (p_df_sales)
A temp table is created from the Parquet data and ran the query (average price per view rating). Runtime is measured and compared to previous queries.

Finally, home_sales is uncached and is verified no longer cached.
