# Healthcare Data Engineering

## Healthcare OLTP to OLAP Data Engineering using MySQL, PySpark and Databricks

### Project Overview

This project implements an end-to-end healthcare data engineering pipeline that transforms normalized healthcare OLTP data into an analytical OLAP Star Schema.

The pipeline performs data ingestion, cleansing, validation, transformation, incremental processing, dimensional modeling, and healthcare analytics using PySpark and Databricks.

### Architecture

MySQL OLTP
↓
PySpark ETL
↓
Bronze Layer
↓
Silver Layer
↓
Gold Star Schema
↓
Healthcare Analytics

### Technologies Used

- MySQL
- MySQL Workbench
- PySpark
- Databricks
- Delta Lake
- SQL
- Python

### Source OLTP Database

The healthcare OLTP database contains 21 normalized tables representing:

- Patients
- Doctors
- Departments
- Appointments
- Diagnoses
- Treatments
- Medications
- Prescriptions
- Laboratory Tests
- Insurance
- Billing
- Payments

Primary keys and foreign keys are used to maintain relationships between the healthcare entities.

### Databricks Pipeline

#### Bronze Layer

Raw healthcare source data is ingested using PySpark and stored as Delta tables.

#### Silver Layer

The data is cleaned and validated using:

- Duplicate removal
- String standardization
- NULL validation
- Date validation
- Referential integrity checks

#### Gold Layer

The normalized OLTP structure is transformed into a Star Schema.

### Dimension Tables

- dim_date
- dim_patient
- dim_doctor
- dim_department
- dim_diagnosis
- dim_treatment
- dim_medication
- dim_insurance

### Fact Tables

- fact_patient_visits
- fact_treatments
- fact_prescriptions
- fact_lab_tests
- fact_billing
- fact_insurance_claims

### Slowly Changing Dimensions

The project demonstrates:

- SCD Type 1 — Patient
- SCD Type 2 — Doctor
- SCD Type 3 — Doctor

### Data Quality

The pipeline includes:

- Bronze-to-Silver reconciliation
- Duplicate detection
- NULL validation
- Referential integrity validation
- Invalid-date detection
- Financial validation
- Fact-table reconciliation

### Incremental / CDC Processing

A watermark-based incremental processing mechanism was implemented using the `updated_at` timestamp.

The pipeline identifies only records that have changed after the previously processed timestamp.

A controlled CDC demonstration successfully detected one changed appointment and updated the watermark.

### Healthcare Analytics

The analytical layer provides:

- Patient visit analysis
- Doctor performance
- Department performance
- Treatment analysis
- Treatment outcomes
- Medication usage
- Lab testing analysis
- Hospital revenue
- Billing analysis
- Billing trends
- Insurance claims
- Disease and diagnosis trends
- Healthcare KPIs

### Project Notebooks

| Notebook | Purpose |
|---|---|
| 01_Bronze_Ingestion | Source data ingestion |
| 02_Silver_Transformation | Data cleansing and transformation |
| 03_Gold_Star_Schema | Star Schema and SCD implementation |
| 04_Data_Quality | Data quality and reconciliation |
| 05_Incremental_CDC | Incremental / CDC processing |
| 06_Healthcare_Analytics | Healthcare analytics and KPIs |

### Repository Structure

```text
Healthcare-Data-Engineering/
│
├── mysql/
│   └── healthcare_oltp.sql
│
├── databricks/
│   ├── 01_Bronze_Ingestion.py
│   ├── 02_Silver_Transformation.py
│   ├── 03_Gold_Star_Schema.py
│   ├── 04_Data_Quality.py
│   ├── 05_Incremental_CDC.py
│   └── 06_Healthcare_Analytics.py
│
├── documentation/
│   └── Healthcare_Data_Engineering_Full_Implementation_Explanation.docx
│
└── screenshots/
