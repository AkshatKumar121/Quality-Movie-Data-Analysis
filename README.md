📽️ Quality Movie Data Analysis
An Industrial-Grade Data Ingestion & Quality Processing Pipeline using AWS
🚀 Project Overview

The Quality Movie Data Analysis project focuses on designing and implementing a scalable, automated, and quality-driven data ingestion pipeline using AWS services.
The goal is to ingest only high-quality movie data into the Amazon Redshift Data Warehouse by validating datasets at every stage and ensuring only trusted data is available for analytics.

🏗️ Architecture

Tech Stack Used:

Amazon S3 – Raw & processed movie dataset storage

AWS Glue Crawler – Schema inference & table creation in Glue Catalog

AWS Glue Data Catalog – Central metadata store

AWS Glue Data Quality – Validation and data-quality rule checks

AWS Glue Low-Code ETL – Data transformations & quality filtering

Amazon Redshift – Final analytical data warehouse

Amazon EventBridge – Automated pipeline triggering

Amazon SNS – Notification for pipeline success/failure

📂 Folder Structure
Quality-Movie-Data-Analysis/
│
├── data/
│   ├── raw/                 # Raw movie dataset stored in S3
│   ├── processed/           # Cleaned and high-quality data
│
├── glue-scripts/
│   ├── etl_quality_job.py   # Low-code + custom transformations
│
├── config/
│   ├── dq_rules.json        # Glue Data Quality rule set
│
├── sql/
│   ├── redshift_schema.sql  # Table creation for Redshift
│
└── README.md

🔧 Pipeline Workflow
1️⃣ Upload Data to S3

Raw movie files (CSV/JSON/Parquet) are uploaded to the S3 raw bucket.

2️⃣ Cataloging with Glue Crawler

Glue Crawler scans the S3 raw file

Automatically detects schema

Creates metadata tables in Glue Data Catalog

3️⃣ Apply Data Quality Checks

Using Glue Data Quality, rules such as:

Non-null checks

Valid range constraints (ratings, release year)

Referential checks

Duplicate record checks

Only high-quality records pass through to the next stage.

4️⃣ Transform using Glue Low-Code ETL

Clean bad records

Standardize column formats

Filter invalid rows

Generate curated dataset

5️⃣ Load High-Quality Data into Redshift

Curated dataset is inserted into Redshift fact & dimension tables.

6️⃣ EventBridge Automation

EventBridge triggers the Glue ETL job when:

New files land in S3

Scheduled ingestion events occur

7️⃣ SNS Notifications

SNS sends success/failure alerts to email subscribers.

📊 Outcome

✔ Ensures only validated, high-quality movie data reaches Redshift
✔ Automated ingestion pipeline requiring no manual intervention
✔ Metadata-driven processing with schema evolution support
✔ Fully scalable and serverless architecture

🛠️ How to Run the Project

Upload your movie dataset to the S3 raw bucket.

Run the Glue Crawler to create/update metadata.

Trigger the Glue ETL Quality Job manually or via EventBridge.

After successful completion, query the processed data in Amazon Redshift.