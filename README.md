# Data Engineering Nanodegree 

A few projects done in Udacity Data Engineering Nanodegree

### Project 1 - Data Model with Postgres
- Design a database and build ETL pipeline to move data from JSON file to Postgres database
  - Extract data from JSON file using pandas dataframe
  - Insert data into Postgres Database using psycopg2

### Project 2 - Data Model with Cassandra
- With Apache Cassandra model the database tables on the queries you want to run

### Project 3 - Data Warehouse 
- Build an ETL pipeline:
  - Extracts data from S3 and stages them in Redshift using COPY command
  - Transforms data into a set of dimensional tables 

### Project 4 - Data Lake
- Building an ETL pipeline:
  - Extracts data from S3 using spark.read.json
  - Processes data using Spark
  - Loads the data back into S3 as a set of dimensional table

### Project 5 - Data Pipeline with Airflow
- Use the Apache Airflow to make more automation and monitoring to the data warehouse ETL pipelines
  - Create and configure DAG
  - Build different operators 
    - Create tables Operator
    - Stage Operator 
    - Fact and Dimension Operators
    - Data Quality Operator
- Data pipelines with airflow:
  - Dynamic and built from reusable tasks
  - Can be monitored
  - Allow easy backfills
