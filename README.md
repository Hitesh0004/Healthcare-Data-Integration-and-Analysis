# Healthcare-Data-Integration-and-Analysis

## Project Overview

This project was completed as part of the **Foundations of Healthcare Data Analytics** course, which is one of the three courses in the **Introduction to Healthcare Data Analytics** learning pathway.

The project demonstrates my understanding of how healthcare data is captured, stored, exchanged, prepared and analysed to support clinical, operational and financial decision-making.

The main focus of this project is to work with multi-source healthcare datasets, including:

* Electronic Health Record data
* Pharmacy claims data
* Lab results data

Using **Excel, Python and SQL**, I imported raw healthcare files, performed data quality checks, cleaned and standardised patient data, and queried linked datasets to generate useful insights.

---

## Healthcare Data Journey

Healthcare analytics is not only about analysing a dataset. It starts much earlier in the data lifecycle.

This project follows the healthcare data journey across four stages:

### 1. Data Capture

Healthcare data begins when a patient interacts with the healthcare system.

For example, a patient visiting a clinic for a Type 2 Diabetes review may generate:

* Patient demographics
* Date of birth
* Gender
* Diagnosis information
* Lab test results
* Medication claims
* Billing or payer records

### 2. Data Storage

The captured data is stored across different healthcare systems.

For example:

* Demographics and chronic conditions are stored in the EHR system
* Lab results are stored in laboratory systems
* Medication fills and paid amounts are stored in pharmacy or claims systems

Because no single system contains the full patient story, healthcare analytics often requires careful data integration.

### 3. Data Exchange

Healthcare systems need standards to communicate accurately.

Examples include:

* **HL7** for healthcare messaging
* **FHIR** for API-based data exchange
* **ICD-10** for diagnosis classification
* **CPT** for procedure and billing activity
* **SNOMED CT** for clinical concepts
* **LOINC** for lab test observations

These standards help ensure that patient data can move between systems in a consistent and meaningful way.

### 4. Data Analysis

Once the data is imported, cleaned and validated, it can be analysed using tools such as Excel, Python and SQL.

In this project, the analysis focused on:

* Pharmacy claim payments
* Payer-level payment totals
* LDL Cholesterol results
* Patients with specific chronic conditions
* Lab test results linked to patient records
* Patient and payer relationships

---

## Key Concepts Covered

### Healthcare Data Sources

This project helped me understand different types of healthcare data:

| Data Type                 | Example                                                         |
| ------------------------- | --------------------------------------------------------------- |
| Electronic Health Records | PatientID, DateOfBirth, Gender, PrimaryCondition, AdmissionDate |
| Claims Data               | Payer, paid amount, medication claim                            |
| Lab Data                  | LDL Cholesterol test name and result value                      |
| Pharmacy Data             | Medication fills and payer information                          |
| Clinical Trial Data       | Trial group, baseline condition, follow-up result               |

---

## Healthcare Standards and Coding Systems

Healthcare data needs standardisation so that different systems can describe the same clinical event consistently.

| Standard  | Purpose                        | Example                                              |
| --------- | ------------------------------ | ---------------------------------------------------- |
| ICD-10    | Diagnosis classification       | Type 2 Diabetes coded as E11.x                       |
| CPT       | Procedure and billing activity | Consultation or lab procedure billing                |
| SNOMED CT | Clinical concepts              | Asthma, allergy, symptoms or findings                |
| LOINC     | Lab test observations          | LDL Cholesterol test identifier                      |
| HL7       | System messaging               | Lab result sent from lab system to EHR               |
| FHIR      | API-based exchange             | Patient, Observation and MedicationRequest resources |

---

## Privacy and Security Considerations

Healthcare data is highly sensitive, so privacy and responsible handling are essential.

This project considered:

* HIPAA and GDPR principles
* California privacy and medical information laws
* Minimum necessary use of patient data
* De-identification before public sharing
* Removal of personally identifiable information
* Role-based access and auditability
* Confidentiality, integrity and availability

For portfolio and GitHub sharing, this project uses educational/sample data only. No real patient-identifiable information is included.

---

## Tools Used

| Tool         | Purpose                                                                     |
| ------------ | --------------------------------------------------------------------------- |
| Excel        | Importing text files, filtering, sorting, SUMIF, AVERAGEIF and quick checks |
| Python       | Cleaning, validation, standardisation and exporting cleaned data            |
| pandas       | Handling missing values, duplicates, gender values and date formats         |
| SQL          | Querying patients, lab results and pharmacy claims                          |
| Google Colab | Running Python and SQL tasks in notebook format                             |

---

## Hands-on Labs Completed

Before completing the final project, I completed several practical labs.

### 1. Healthcare Coding Standards Lab

I classified clinic records using ICD-10, CPT and SNOMED CT. I also used Excel filters and SUMIF to explore diagnosis, procedure and visit-cost patterns.

### 2. Multi-source Import Lab

I imported healthcare datasets from Excel, CSV/TXT and TSV formats, then performed a basic data pulse check to review structure, completeness and quality.

### 3. Relational SQL Lab

I created and queried linked healthcare tables for patients, visits, diagnoses, billing and lab results using primary and foreign keys.

### 4. Python Cleaning Lab

I cleaned a synthetic healthcare dataset by removing PII, handling missing values, standardising categories, converting mixed formats, treating outliers and preparing the data for analysis.

---

## Final Project Scenario

The final project simulated the role of a Healthcare Data Analyst working for a multi-clinic system.

The organisation was launching a **Population Health Improvement Initiative** focused on:

* Hypertension
* Diabetes
* Osteoarthritis
* High LDL Cholesterol

The leadership team needed a clean and trustworthy dataset combining information from:

* EHR patient records
* Pharmacy claims
* Lab test results

---

## Final Project Tasks

### Part 1: Excel Import and Analysis

I imported raw text-based healthcare files into Excel and analysed them using filters, sorting and formulas.

Tasks completed:

* Imported Pharmacy Claims data
* Imported Lab Results data
* Identified paid amounts greater than $250
* Found the payer with the highest paid amount
* Used SUMIF to calculate total amount paid by payer
* Analysed LDL Cholesterol results
* Used AVERAGEIF to calculate average LDL Cholesterol value
* Identified patients with high LDL Cholesterol values

### Part 2: Python Cleaning and Validation

Using Python, I cleaned the EHR patient dataset.

Tasks completed:

* Identified missing values
* Identified duplicate rows
* Checked inconsistent Gender values
* Checked inconsistent AdmissionDate formats
* Filled missing DateOfBirth and ZipCode values appropriately
* Removed exact duplicate records
* Standardised Gender values:

  * M, male, m → Male
  * F, Female, f → Female
* Standardised AdmissionDate values using pandas
* Converted Excel serial dates such as 45258 into readable date format
* Exported the cleaned dataset as a CSV file

### Part 3: SQL Analysis

Using SQL, I queried linked healthcare datasets.

Queries completed:

* Listed all patients born before 1980
* Listed all female patients with Type 2 Diabetes
* Displayed lab tests with PatientID, Gender, DateOfBirth, TestName and TestResultValue
* Displayed distinct patients with their payer information from pharmacy claims

---

## Sample SQL Queries

### Patients Born Before 1980

```sql
SELECT 
    PatientID,
    DateOfBirth,
    Gender,
    ZipCode,
    PrimaryCondition,
    AdmissionDate
FROM patients
WHERE DATE(DateOfBirth) < '1980-01-01';
```

### Female Patients with Type 2 Diabetes

```sql
SELECT 
    PatientID,
    DateOfBirth,
    Gender,
    ZipCode,
    PrimaryCondition,
    AdmissionDate
FROM patients
WHERE Gender = 'Female'
  AND PrimaryCondition LIKE '%Type 2 Diabetes%';
```

### Lab Tests with Patient Details

```sql
SELECT 
    p.PatientID,
    p.Gender,
    p.DateOfBirth,
    l.TestName,
    l.TestResultValue
FROM patients p
JOIN lab_results l
    ON p.PatientID = l.PatientID;
```

### Distinct Patients with Payer Information

```sql
SELECT DISTINCT
    p.PatientID,
    p.Gender,
    p.DateOfBirth,
    pc.Payer
FROM patients p
JOIN pharmacy_claims pc
    ON p.PatientID = pc.PatientID;
```

---

## Project Workflow

```text
Raw Healthcare Files
        ↓
Excel Import and Initial Analysis
        ↓
Python Data Cleaning and Validation
        ↓
Cleaned EHR Dataset
        ↓
SQL Querying and Data Integration
        ↓
Analysis-ready Healthcare Insights
```

---

## Skills Demonstrated

This project demonstrates the following skills:

* Healthcare data analytics
* Healthcare data lifecycle understanding
* EHR, claims, lab and pharmacy data interpretation
* Healthcare coding and interoperability awareness
* ICD-10, CPT, SNOMED CT, LOINC, HL7 and FHIR understanding
* Healthcare privacy and security awareness
* HIPAA, GDPR and de-identification principles
* Excel data import and analysis
* Python data cleaning with pandas
* SQL querying and joins
* Data quality validation
* Missing value handling
* Duplicate detection and removal
* Date standardisation
* Documentation and project communication

---

## Portfolio Value

This project helped me understand how healthcare data moves from patient care to decision-making.

It also strengthened my ability to:

* Work with multi-source healthcare datasets
* Identify and fix data quality issues
* Prepare healthcare data for analysis
* Apply privacy-aware data handling
* Use Excel, Python and SQL in a practical healthcare scenario
* Communicate technical work clearly for GitHub, LinkedIn and interviews

---

## Repository Structure

```text
Healthcare-Data-Integration-and-Analysis/
│
├── Final Project/
│   ├── Excel analysis files
│   ├── Python cleaning and validation notebook
│   ├── SQL analysis queries
│   ├── cleaned output files
│   └── final project submission/evidence
│
├── Presentation and Certification/
│   ├── project presentation
│   └── course certificate
│
├── Labs/
│   ├── healthcare coding standards lab
│   ├── multi-source import lab
│   ├── relational SQL database lab
│   └── Python cleaning and validation lab
│
└── README.md
```

### Folder Description

**Final Project** contains the main Healthcare Data Integration and Analysis project, including Excel analysis, Python data cleaning, SQL queries, cleaned datasets and final outputs.

**Presentation and Certification** contains the project showcase presentation and the course completion certificate.

**Labs** contains the hands-on lab activities completed during the course, covering healthcare coding standards, multi-source data import, relational SQL databases and Python-based healthcare data cleaning.

**README.md** provides the project overview, healthcare data journey, tools used, key concepts, final project workflow and skills demonstrated.


## Note on Data Privacy

This project is for educational and portfolio purposes only.

The datasets used are sample or synthetic healthcare datasets. No real patient-identifiable information is included. Any personally identifiable information used in practice was removed or de-identified before public sharing.

---

## Author

**Hitesh Rathi**
Sydney, Australia
GitHub: [Healthcare Data Integration and Analysis](https://github.com/Hitesh0004/Healthcare-Data-Integration-and-Analysis)
