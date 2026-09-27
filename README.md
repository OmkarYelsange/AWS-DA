# ☁️ AWS Data Analytics & ETL Pipeline

<p align="center">
  <img src="https://img.shields.io/badge/AWS-Cloud%20Analytics-orange?style=for-the-badge&logo=amazon-aws" />
  <img src="https://img.shields.io/badge/Amazon%20S3-Data%20Lake-red?style=for-the-badge&logo=amazon-s3" />
  <img src="https://img.shields.io/badge/AWS%20Glue-ETL-blue?style=for-the-badge&logo=amazon-aws" />
  <img src="https://img.shields.io/badge/Athena-SQL-orange?style=for-the-badge&logo=amazon-aws" />
  <img src="https://img.shields.io/badge/QuickSight-BI-green?style=for-the-badge&logo=amazon-aws" />
</p>

<p align="center">
  <b>End-to-End Healthcare Data Engineering & Analytics Pipeline on AWS</b>
</p>

---

## 📌 Project Overview

This project demonstrates an **end-to-end cloud data analytics pipeline using AWS services** to process, transform, catalog, query, and visualize healthcare/patient data.

The pipeline follows a practical data engineering workflow:

**Raw Healthcare Data → Amazon S3 → AWS Glue DataBrew → AWS Glue → ETL → Amazon Athena → Amazon QuickSight**

The project focuses on building a scalable cloud-based workflow that converts raw CSV healthcare data into **clean, structured, queryable, and visualization-ready datasets**.

---

## 🎯 Project Objectives

* Build a cloud-based **data lake** using Amazon S3.
* Upload and organize raw healthcare/patient datasets.
* Profile and clean data using **AWS Glue DataBrew**.
* Create a data catalog using **AWS Glue Crawler**.
* Perform ETL operations using **AWS Glue Jobs**.
* Query processed data using **Amazon Athena**.
* Create analytical dashboards using **Amazon QuickSight**.
* Understand an end-to-end **AWS data engineering and analytics workflow**.

---

## 🏗️ Architecture

```text
                    ┌──────────────────────┐
                    │   Healthcare Data    │
                    │      CSV Files       │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │     Amazon S3        │
                    │      Data Lake       │
                    └──────────┬───────────┘
                               │
                               ▼
                 ┌────────────────────────────┐
                 │     AWS Glue DataBrew      │
                 │                            │
                 │  • Data Profiling          │
                 │  • Data Cleaning           │
                 │  • Transformation          │
                 └────────────┬───────────────┘
                              │
                              ▼
                 ┌────────────────────────────┐
                 │       AWS Glue             │
                 │                            │
                 │  • Crawler                 │
                 │  • Data Catalog            │
                 │  • ETL Jobs                │
                 └────────────┬───────────────┘
                              │
                              ▼
                    ┌──────────────────────┐
                    │   Processed Dataset  │
                    │        in S3         │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │    Amazon Athena     │
                    │                      │
                    │    SQL Analytics     │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   Amazon QuickSight  │
                    │                      │
                    │ Dashboards & Reports │
                    └──────────────────────┘
```

---

# 🔄 Data Pipeline

### 1️⃣ Raw Data

The project starts with healthcare/patient data stored in CSV format.

Example datasets included in the repository:

* `patient_data1.csv`
* `patient_data2.csv`

These datasets represent the raw input layer of the pipeline.

---

### 2️⃣ Amazon S3 — Data Lake

Amazon S3 is used as the central storage layer for the project.

The raw datasets are uploaded to an S3 bucket and organized into appropriate folders.

Example structure:

```text
S3 Bucket
│
├── raw-data/
│   ├── patient_data1.csv
│   └── patient_data2.csv
│
├── processed-data/
│
└── output/
```

### Key responsibilities

* Store raw healthcare data.
* Maintain processed datasets.
* Provide scalable and durable cloud storage.
* Act as the foundation of the AWS data lake.

---

# 🧹 AWS Glue DataBrew

AWS Glue DataBrew is used for **visual data preparation and transformation**.

The raw healthcare dataset can be profiled to understand:

* Missing values
* Duplicate records
* Data types
* Invalid values
* Outliers
* Column distributions
* Data quality issues

### Data preparation activities

Typical transformations include:

* Removing duplicate records
* Handling missing values
* Correcting data types
* Standardizing column values
* Renaming columns
* Filtering invalid records
* Preparing data for downstream analytics

---

# 🕷️ AWS Glue Crawler

AWS Glue Crawler automatically analyzes the data stored in Amazon S3 and creates metadata in the **AWS Glue Data Catalog**.

The crawler identifies:

* Tables
* Columns
* Data types
* Data locations
* Dataset structure

This allows services such as Amazon Athena to understand and query the dataset.

### Workflow

```text
S3 Dataset
     │
     ▼
AWS Glue Crawler
     │
     ▼
Glue Data Catalog
     │
     ▼
Athena
```

---

# ⚙️ AWS Glue ETL

AWS Glue is used to perform the **Extract, Transform, Load (ETL)** process.

### ETL Flow

```text
Extract
   ↓
Read raw data from S3
   ↓
Transform
   ↓
Clean + Standardize + Process
   ↓
Load
   ↓
Write processed data back to S3
```

### ETL responsibilities

* Extract data from S3.
* Apply transformations.
* Convert data into analytics-ready format.
* Write processed datasets to the target S3 location.
* Update/catalog the resulting dataset.

---

# 🔎 Amazon Athena

Amazon Athena is used to perform **serverless SQL analysis directly on data stored in Amazon S3**.

Example analytical queries:

```sql
SELECT *
FROM patient_data
LIMIT 10;
```

### Example aggregation

```sql
SELECT
    gender,
    COUNT(*) AS patient_count
FROM patient_data
GROUP BY gender;
```

### Example analysis

```sql
SELECT
    department,
    COUNT(*) AS total_patients
FROM patient_data
GROUP BY department
ORDER BY total_patients DESC;
```

Athena provides a convenient SQL interface for exploring the processed healthcare dataset without managing database infrastructure.

---

# 📊 Amazon QuickSight

Amazon QuickSight is used as the **business intelligence and visualization layer**.

The processed data can be connected to QuickSight to create interactive dashboards.

### Possible dashboard components

* 👥 Total Patients
* 📈 Patient Distribution
* 🏥 Department-wise Analysis
* ⚕️ Patient Demographics
* 📊 Category-wise Metrics
* 📅 Time-based Trends
* 🔍 Filterable Analytical Views

Example dashboard workflow:

```text
S3
 ↓
Glue ETL
 ↓
Athena
 ↓
QuickSight
 ↓
Interactive Dashboard
```

---

# 🗂️ Repository Structure

```text
AWS-DA/
│
├── Pics/
│   └── Project screenshots
│
├── patient_data1.csv
├── patient_data2.csv
│
└── README.md
```

---

# 🛠️ AWS Services Used

| AWS Service           | Purpose                                  |
| --------------------- | ---------------------------------------- |
| **Amazon S3**         | Cloud storage and data lake              |
| **AWS Glue DataBrew** | Data profiling, cleaning and preparation |
| **AWS Glue Crawler**  | Schema discovery and Data Catalog        |
| **AWS Glue**          | ETL processing                           |
| **Amazon Athena**     | Serverless SQL analytics                 |
| **Amazon QuickSight** | Data visualization and dashboards        |

---

# 🧰 Technologies & Concepts

### Cloud

* Amazon Web Services (AWS)
* Amazon S3
* AWS Glue
* AWS Glue DataBrew
* Amazon Athena
* Amazon QuickSight

### Data Engineering

* Data Lake
* ETL / ELT
* Data Cleaning
* Data Transformation
* Data Cataloging
* Schema Discovery
* Data Quality
* Serverless Analytics

### Analytics

* SQL
* Data Aggregation
* Exploratory Data Analysis
* Business Intelligence
* Dashboard Development
* Data Visualization

---

# 🚀 End-to-End Implementation

## Step 1 — Prepare the Dataset

Download or use the healthcare CSV datasets provided in this repository.

```text
patient_data1.csv
patient_data2.csv
```

---

## Step 2 — Create an S3 Bucket

Create an Amazon S3 bucket and organize the data into logical folders.

Recommended structure:

```text
bucket-name/
│
├── raw/
├── processed/
└── output/
```

Upload the raw CSV files into the `raw/` directory.

---

## Step 3 — Profile Data Using DataBrew

Create a DataBrew dataset using the S3 source.

Perform data profiling to identify:

* Missing values
* Duplicate records
* Incorrect data types
* Invalid values
* Data inconsistencies

Create a transformation recipe and apply the required cleaning operations.

---

## Step 4 — Create AWS Glue Crawler

Create a Glue Crawler pointing to the relevant S3 location.

Configure:

```text
Data Source
     ↓
Amazon S3
     ↓
Crawler
     ↓
Glue Data Catalog
```

Run the crawler and verify that the table has been created successfully.

---

## Step 5 — Create Glue ETL Job

Create an AWS Glue ETL job to process the data.

The ETL job should:

1. Read source data.
2. Apply transformations.
3. Perform data cleaning.
4. Convert the data into a structured format.
5. Write the processed dataset to S3.

---

## Step 6 — Query Using Athena

Open Amazon Athena and select the Glue Data Catalog database.

Run SQL queries against the processed dataset.

Example:

```sql
SELECT COUNT(*) AS total_records
FROM patient_data;
```

Then perform additional aggregations and analytical queries based on the available columns.

---

## Step 7 — Build QuickSight Dashboard

Connect Amazon QuickSight to the analytical dataset.

Create visualizations such as:

```text
KPI Cards
     ↓
Charts
     ↓
Filters
     ↓
Aggregations
     ↓
Interactive Dashboard
```

Use the dashboard to communicate meaningful insights from the healthcare dataset.

---

# 📈 Key Learning Outcomes

Through this project, the following practical concepts were implemented:

* Building an AWS-based data pipeline
* Creating a cloud data lake using S3
* Performing data preparation using DataBrew
* Using Glue Crawlers for schema discovery
* Creating a centralized Data Catalog
* Building ETL workflows using AWS Glue
* Querying S3 data using Athena
* Creating BI dashboards using QuickSight
* Understanding the relationship between data engineering and analytics
* Working with healthcare-oriented datasets in a cloud environment

---

# 🔐 Security Considerations

For a real-world healthcare analytics implementation, additional security controls would be required.

Important considerations include:

* IAM least-privilege access
* S3 bucket policies
* Encryption at rest
* Encryption in transit
* Secure credential management
* CloudTrail auditing
* Data masking/anonymization
* Access control for dashboards
* Protection of sensitive healthcare information

> **Note:** The datasets in this educational project should not be treated as production healthcare data. Any real patient information must be handled according to applicable privacy, security, and regulatory requirements.

---

# 💡 Future Improvements

Potential improvements to this project include:

* [ ] Add automated AWS Glue ETL workflows.
* [ ] Convert CSV data into Parquet format.
* [ ] Implement partitioning for improved Athena performance.
* [ ] Add AWS Lambda-based automation.
* [ ] Add Amazon CloudWatch monitoring.
* [ ] Implement automated data-quality checks.
* [ ] Add scheduled ETL pipelines.
* [ ] Build a more advanced QuickSight dashboard.
* [ ] Implement IAM least-privilege policies.
* [ ] Add infrastructure-as-code using AWS CloudFormation or Terraform.
* [ ] Add CI/CD automation for data pipeline deployment.

---

# 📸 Project Screenshots

Project screenshots and implementation references are available in the [`Pics`](./Pics) directory.

Suggested screenshots to include:

1. Amazon S3 bucket
2. S3 folder structure
3. DataBrew dataset
4. DataBrew profile
5. DataBrew transformation recipe
6. Glue Crawler
7. Glue Data Catalog
8. Glue ETL Job
9. Athena SQL queries
10. QuickSight dashboard

---

# 🧠 Architecture Summary

The project implements a complete cloud analytics workflow:

```text
                 RAW DATA
                    │
                    ▼
              ┌───────────┐
              │ Amazon S3 │
              └─────┬─────┘
                    │
                    ▼
          ┌──────────────────┐
          │ AWS Glue DataBrew│
          └────────┬─────────┘
                   │
                   ▼
            ┌─────────────┐
            │ AWS Glue    │
            │ Crawler     │
            └──────┬──────┘
                   │
                   ▼
          ┌─────────────────┐
          │ Glue Data       │
          │ Catalog         │
          └────────┬────────┘
                   │
                   ▼
            ┌─────────────┐
            │ AWS Glue    │
            │ ETL         │
            └──────┬──────┘
                   │
                   ▼
             ┌──────────┐
             │   S3     │
             │ Processed│
             │   Data   │
             └─────┬────┘
                   │
                   ▼
            ┌─────────────┐
            │   Athena    │
            │ SQL Queries │
            └──────┬──────┘
                   │
                   ▼
           ┌────────────────┐
           │  QuickSight    │
           │   Dashboard    │
           └────────────────┘
```

---

# 👨‍💻 Author

**Omkar Yelsange**

B.E. Robotics & Automation Engineering
Data Analytics | Data Engineering | AWS | SQL | Python

### Connect With Me

* 💼 **LinkedIn:** [Omkar Yelsange](https://www.linkedin.com/)
* 🐙 **GitHub:** [OmkarYelsange](https://github.com/OmkarYelsange)

---

# ⭐ Project

If you find this project useful or helpful for learning AWS Data Analytics, consider giving the repository a ⭐.

**Repository:**
https://github.com/OmkarYelsange/AWS-DA

---

<p align="center">
  <b>Built with ☁️ AWS • 📊 Data Analytics • 🛠️ Data Engineering</b>
</p>
