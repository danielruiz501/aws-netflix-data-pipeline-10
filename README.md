# AWS Netflix Data Pipeline

![AWS](https://img.shields.io/badge/AWS-Cloud-orange?logo=amazonaws)
![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Apache Spark](https://img.shields.io/badge/Apache%20Spark-3.5-orange?logo=apachespark)
![SQL](https://img.shields.io/badge/SQL-Analytics-blue?logo=postgresql)
![Amazon S3](https://img.shields.io/badge/Amazon%20S3-Data%20Lake-orange?logo=amazons3)
![AWS Glue](https://img.shields.io/badge/AWS%20Glue-ETL-orange?logo=amazonaws)
![Amazon Athena](https://img.shields.io/badge/Amazon%20Athena-SQL%20Analytics-blue?logo=amazonaws)
![Amazon Redshift](https://img.shields.io/badge/Amazon%20Redshift-Data%20Warehouse-red?logo=amazonredshift)
![AWS DMS](https://img.shields.io/badge/AWS%20DMS-Data%20Migration-orange?logo=amazonaws)
![CloudWatch](https://img.shields.io/badge/Amazon%20CloudWatch-Monitoring-purple?logo=amazonaws)
![License](https://img.shields.io/badge/License-MIT-green)

## 📌 Overview

End-to-end AWS data engineering pipeline built with Netflix data, demonstrating data ingestion, migration, ETL, data lake storage, analytics, data warehousing, and cloud monitoring.

## 🏗️ Architecture

![AWS Architecture](./architecture.png)

## Data Flow


Netflix Dataseta
      ↓
Amazon RDS MySQL
      ↓
AWS DMS
      ↓
Amazon S3
      ↓
AWS Glue + Apache Spark
      ↓
Parquet
      ↓
Amazon Athena
      ↓
Amazon Redshift Serverless
      ↓
SQL Analytics

Amazon CloudWatch
      ↓
Monitoring

## 🎯 Project Objectives

- Build an end-to-end AWS data engineering pipeline.
- Ingest Netflix data into Amazon RDS MySQL.
- Migrate data from RDS to Amazon S3 using AWS DMS.
- Transform raw data into Parquet using AWS Glue and Apache Spark.
- Catalog and query processed data with AWS Glue Data Catalog and Amazon Athena.
- Load Parquet data into Amazon Redshift Serverless.
- Perform analytical SQL queries on the Netflix dataset.
- Monitor the Redshift workload using Amazon CloudWatch.
- Practice AWS data engineering, ETL, data lake, and data warehouse concepts.
- Apply AWS resource cleanup and cost-control practices.

## ☁️ AWS Services Used

| AWS Service | Purpose |
|---|---|
| Amazon RDS for MySQL | Source relational database for the Netflix dataset |
| AWS DMS | Migrates Netflix data from MySQL to Amazon S3 |
| Amazon S3 | Data lake storage for raw and processed data |
| AWS Glue | Data cataloging and ETL processing |
| Apache Spark | Data transformation within AWS Glue |
| Apache Parquet | Columnar storage format for analytics |
| Amazon Athena | Serverless SQL queries over data in S3 |
| Amazon Redshift Serverless | Data warehouse for analytical workloads |
| Amazon CloudWatch | Monitoring and observability |

## 🛠️ Technologies

- **Database:** MySQL
- **Programming Language:** Python
- **Data Processing:** Apache Spark / PySpark
- **Storage Format:** Apache Parquet
- **Query Language:** SQL
- **Cloud Platform:** Amazon Web Services (AWS)
- **Data Migration:** AWS Database Migration Service (DMS)
- **ETL:** AWS Glue
- **Analytics:** Amazon Athena and Amazon Redshift
- **Monitoring:** Amazon CloudWatch
- **Version Control:** Git / GitHub

## 🔄 Project Workflow

#### 1. Netflix Dataset
The Netflix dataset was used as the primary data source for the project.

#### 2. Amazon RDS MySQL
A MySQL database was created in Amazon RDS and populated with the Netflix dataset.

#### 3. AWS DMS
AWS Database Migration Service was configured to migrate the Netflix data from Amazon RDS MySQL to Amazon S3.

#### 4. Amazon S3
Amazon S3 was used as the data lake to store the raw Netflix data and the processed Parquet files.

#### 5. AWS Glue + Apache Spark
AWS Glue was used to process the data with PySpark and convert the source data into the optimized Parquet format.

#### 6. AWS Glue Data Catalog
A Glue crawler was used to discover and catalog the Parquet schema.

#### 7. Amazon Athena
Amazon Athena was used to query the Parquet data directly from Amazon S3 using SQL.

#### 8. Amazon Redshift Serverless
The processed Parquet data was loaded into Amazon Redshift Serverless for data warehouse analytics.

#### 9. SQL Analytics
Analytical queries were executed to analyze Netflix content by type, release year, country, and total records.

#### 10. Amazon CloudWatch
Amazon CloudWatch metrics were used to monitor the Redshift workload and successful queries.

## 📁 Project Structure

```text
aws-netflix-data-pipeline-10/
│
├── architecture.png
├── netflix_titles.csv
├── LICENSE
├── README.md
│
└── screenshots/
    ├── 01-project-files.png
    ├── 02-rds-mysql-source.png
    ├── 03-rds-connectivity-security.png
    ├── 04-mysql-workbench-rds-connection.png
    ├── ...
    ├── 34-redshift-create-netflix-table-fixed.png
    ├── 35-redshift-copy-parquet-success.png
    ├── 36-redshift-select-netflix-data.png
    ├── 37-redshift-analysis-by-type.png
    ├── 38-redshift-analysis-by-release-year.png
    ├── 39-redshift-analysis-by-country.png
    ├── 40-redshift-total-records.png
    └── 41-cloudwatch-redshift-metrics.png

    
```
    
## Implementation


#### 1. Netflix Dataset

The project started with a Netflix dataset containing information about movies and TV shows, including titles, genres, countries, release years, ratings, and descriptions.

#### 2. Amazon RDS MySQL



An Amazon RDS MySQL instance was created as the source relational database. The Netflix dataset was imported into a MySQL database and stored in the `netflix_titles` table.

#### 3. AWS DMS

AWS Database Migration Service was configured to migrate the Netflix data from Amazon RDS MySQL to Amazon S3.

The migration included:

- DMS replication instance
- MySQL source endpoint
- Amazon S3 target endpoint
- Table mapping and selection rules
- Full load task
- Migration monitoring

#### 4. Amazon S3

Amazon S3 was used as the data lake to store the Netflix data migrated by AWS DMS.

The S3 data was then used as the input for the AWS Glue ETL process.

#### 5. AWS Glue + Apache Spark

AWS Glue was used to process the Netflix data stored in Amazon S3.

A PySpark ETL job was created to:

- Read the Netflix data from Amazon S3.
- Process and transform the dataset.
- Convert the data into Apache Parquet format.
- Store the processed data in Amazon S3.
- Prepare the data for analytical queries.

The Glue job completed successfully using Apache Spark.

#### 6. AWS Glue Data Catalog

An AWS Glue crawler was configured to discover the schema of the processed Parquet data.

The crawler created a table in the `netflix_data` database, making the processed dataset available for analytical services.

#### 7. Amazon Athena

Amazon Athena was used to query the processed Parquet data directly from Amazon S3 using SQL.

The following analyses were performed:

- Netflix content by type.
- Titles by release year.
- Titles by country.
- Dataset content validation.

Athena successfully queried the processed Parquet dataset stored in Amazon S3.

#### 8. Amazon Redshift Serverless

Amazon Redshift Serverless was configured as the data warehouse for the processed Netflix dataset.

A `netflix_titles` table was created to store the Parquet data loaded from Amazon S3.

The data was successfully loaded using the Redshift `COPY` command.

#### 9. SQL Analytics

SQL queries were executed in Amazon Redshift to analyze the Netflix dataset.

The analysis included:

- Total number of Netflix records.
- Content distribution by type.
- Titles by release year.
- Titles by country.

These queries demonstrated analytical workloads using Amazon Redshift Serverless.

#### 10. Amazon CloudWatch

Amazon CloudWatch was used to monitor the Redshift Serverless workload.

The `QueriesSucceeded` metric was reviewed for the `netflix-data-workgroup` to verify successful query activity during the analytical phase.

#### 11. Results

The pipeline successfully processed the Netflix dataset through the complete AWS data engineering workflow.

Key results:

- **101 Netflix records** successfully loaded into Amazon Redshift.
- Data successfully transformed into **Apache Parquet**.
- Processed data successfully queried using **Amazon Athena**.
- Analytical SQL queries successfully executed in **Amazon Redshift Serverless**.
- Redshift workload activity successfully monitored using **Amazon CloudWatch**.

## 📸 Screenshots

The following screenshots document the main stages of the AWS data engineering pipeline.

#### Amazon RDS MySQL

![RDS MySQL Source](./screenshots/02-rds-mysql-source.png)

![MySQL Netflix Database](./screenshots/05-mysql-netflix-database.png)

![Netflix Data in MySQL](./screenshots/08-rds-mysql-netflix-data.png)

#### AWS DMS

![DMS Replication Instance](./screenshots/11-dms-replication-instance-available.png)

![DMS MySQL Endpoint](./screenshots/12-dms-mysql-endpoint-successful.png)

![DMS Migration Completed](./screenshots/17-dms-task-load-completed.png)

#### Amazon S3

![Netflix Data in S3](./screenshots/18-s3-dms-netflix-data.png)

#### AWS Glue

![Glue ETL Job](./screenshots/22-glue-job-succeeded.png)

![Parquet Output](./screenshots/23-s3-parquet-output.png)

![Glue Crawler](./screenshots/24-glue-parquet-crawler-succeeded.png)

#### Amazon Athena

![Athena Query](./screenshots/25-athena-netflix-query.png)

![Athena Content Type Analysis](./screenshots/29-athena-content-type-analysis.png)

![Athena Release Year Analysis](./screenshots/30-athena-titles-by-release-year.png)

![Athena Country Analysis](./screenshots/31-athena-titles-by-country.png)

#### Amazon Redshift Serverless

![Redshift Table Creation](./screenshots/34-redshift-create-netflix-table-fixed.png)

![Redshift COPY Parquet](./screenshots/35-redshift-copy-parquet-success.png)

![Redshift Netflix Data](./screenshots/36-redshift-select-netflix-data.png)

![Redshift Analysis by Type](./screenshots/37-redshift-analysis-by-type.png)

![Redshift Analysis by Release Year](./screenshots/38-redshift-analysis-by-release-year.png)

![Redshift Analysis by Country](./screenshots/39-redshift-analysis-by-country.png)

![Redshift Total Records](./screenshots/40-redshift-total-records.png)

#### Amazon CloudWatch

![CloudWatch Redshift Metrics](./screenshots/41-cloudwatch-redshift-metrics.png)

## 💻 SQL Queries

The following SQL queries were executed in Amazon Redshift Serverless.

#### Total Netflix Records

```sql
SELECT COUNT(*) AS total_records
FROM netflix_titles;
```
#### Content Distribution by Type

```sql
SELECT
    type,
    COUNT(*) AS total_titles
FROM netflix_titles
GROUP BY type
ORDER BY total_titles DESC;
**Result:**
- Movie: 56
- TV Show: 45

**Result:**
- Movie: 56
- TV Show: 45

```

#### Titles by Release Year

```sql
SELECT
    release_year,
    COUNT(*) AS total_titles
FROM netflix_titles
GROUP BY release_year
ORDER BY release_year DESC;
**Result:**

The query shows the number of Netflix titles available for each release year, with the most recent years displayed first.
```
![Redshift Analysis by Release Year](./screenshots/38-redshift-analysis-by-release-year.png)

#### Titles by Country

```sql
SELECT
    country,
    COUNT(*) AS total_titles
FROM netflix_titles
WHERE country IS NOT NULL
  AND country <> ''
GROUP BY country
ORDER BY total_titles DESC
LIMIT 10;

**Result:**

The query identifies the countries with the highest number of titles in the dataset.
```
![Redshift Analysis by Country](./screenshots/39-redshift-analysis-by-country.png)

#### Data Validation

```sql
SELECT COUNT(*) AS total_records
FROM netflix_titles;

**Result:**

The query confirms that the Redshift table contains **101 records** after the ETL pipeline.
```
![Redshift Total Records](./screenshots/40-redshift-total-records.png)

## 📊 Key Results

- Successfully migrated Netflix data from MySQL to Amazon S3 using AWS DMS.
- Transformed CSV data into optimized Parquet format using AWS Glue and Apache Spark.
- Cataloged the processed data using the AWS Glue Data Catalog.
- Queried the dataset using Amazon Athena.
- Loaded 101 records into Amazon Redshift Serverless using Parquet.
- Performed analytical queries using Amazon Redshift SQL.
- Monitored Redshift activity using Amazon CloudWatch.

## 🎓 Lessons Learned

This project provided hands-on experience with:

- Designing an end-to-end AWS data engineering pipeline.
- Migrating data using AWS Database Migration Service (DMS).
- Building ETL processes with AWS Glue and Apache Spark.
- Converting CSV data into Parquet for more efficient analytics.
- Using the AWS Glue Data Catalog for schema management.
- Querying data with Amazon Athena and Amazon Redshift.
- Working with Redshift Serverless and loading Parquet data.
- Monitoring AWS workloads using Amazon CloudWatch.
- Troubleshooting schema mismatches and data type compatibility issues.

## 🏁 Conclusion

This project demonstrates an end-to-end AWS data engineering pipeline, from data ingestion and migration to transformation, storage, analytics, and monitoring.

The pipeline integrates Amazon RDS, AWS DMS, Amazon S3, AWS Glue, Apache Spark, Amazon Athena, Amazon Redshift Serverless, and Amazon CloudWatch to create a scalable and analytics-ready data workflow.

This project strengthened my practical experience with AWS Data Engineering, ETL processes, data migration, SQL analytics, and cloud monitoring.

## 📬 Contact

**Daniel Ruiz Lopez**  
AWS Data Engineer

📱 **WhatsApp:** +52 229 172 8291  
📧 **Email:** danielruizlopez889@gmail.com  
💼 **LinkedIn:** [linkedin.com/in/danielruizl](https://www.linkedin.com/in/danielruizl)  
💻 **GitHub:** [github.com/danielruiz501](https://github.com/danielruiz501)

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](./LICENSE) file for details.



