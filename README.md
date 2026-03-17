
# Talend Data Integration Projects

This repository contains several **ETL and data orchestration workflows built using Talend**.
The projects demonstrate common data engineering tasks including **data generation, transformation, file processing, extraction, and loading into databases**.

---

# Project 1 — Transforming and Loading Data into Database

### Overview

This workflow demonstrates a **complete ETL pipeline** where synthetic data is generated, transformed, stored in a temporary file, and finally loaded into a database.
![Transforming and loading data into Database](https://github.com/user-attachments/assets/12ed1829-99d8-459a-8e2e-6c68ce3976bd)

### Workflow Steps

**1. PreJob Initialization**

* The job starts with a **tPrejob** component.
* A **temporary file is created** using `tCreateTemporaryFile`.
* This file will store intermediate transformed data.

**2. Generate and Transform Data**

* `tRowGenerator` generates sample records.
* `tMap` performs data transformation and mapping.
* The transformed data is written to a temporary CSV file using `tFileOutputDelimited`.

**3. Load Data into Database**

* The temporary file is read using `tFileInputDelimited`.
* The processed records are inserted into a **target database table**.

### Key Concepts Demonstrated

* ETL pipeline design
* Temporary data staging
* Data transformation with `tMap`
* Loading structured data into databases

---

# Project 2 — Customer Data Orchestration

### Overview

This project simulates a **customer data processing pipeline** that generates synthetic customer data, enriches it with reference data, and separates valid and rejected records.
![Customer Data Orchasteration](https://github.com/user-attachments/assets/f3a336bf-2ed2-4d5c-9c8b-65332b27cb41)

### Workflow Steps

**1. PreJob Configuration**

* Initializes the job environment.
* Sets global variables using `tSetGlobalVar`.
* Prepares file names and configuration parameters.

**2. Write Header Information**

* A header row is written to the output file to define column structure.

**3. Generate Customer Data**

* `tRowGenerator` creates synthetic customer records including:

  * Customer ID
  * First Name
  * Last Name
  * State ID
  * Birthdate

**4. Data Enrichment**

* `CustomerTable` provides reference data.
* `tMap` joins generated records with state lookup data.

**5. Output Routing**

* Valid customer records are written to the **main output file**.
* Invalid records are redirected to a **reject file** for further inspection.

### Key Concepts Demonstrated

* Data enrichment using lookup tables
* Data validation and reject flows
* File generation and routing
* Talend orchestration with multiple components

---

# Project 3 — Data Extraction and File Processing

### Overview

This project focuses on **extracting and parsing data from different file formats** including JSON, XML, positional, and delimited files.
![Data Extraction Project](https://github.com/user-attachments/assets/0a47db3c-0a94-4795-af15-3ae5ee721869)

### Workflow Steps

**1. File Creation**

* Synthetic data files are generated in multiple formats:

  * JSON
  * XML
  * Positional text
  * Delimited CSV

**2. Data Extraction Modules**

The workflow demonstrates multiple Talend extraction techniques:

**JSON Extraction**

* `tExtractJSONFields` extracts structured fields from JSON documents.

**XML Extraction**

* `tExtractXMLField` parses XML data using XPath expressions.

**Positional File Extraction**

* `tExtractPositionalFields` reads fixed-width file formats.

**Delimited File Extraction**

* `tExtractDelimitedFields` processes CSV-style structured data.

**3. Regex Processing**

* `tExtractRegexFields` extracts specific patterns from text fields.
* Example: splitting email addresses into **prefix and domain**.

**4. Cleanup**

* Temporary files created during the workflow are deleted using `tFileDelete`.

### Key Concepts Demonstrated

* Multi-format data ingestion
* Structured and semi-structured data parsing
* Regex-based field extraction
* End-to-end file processing pipelines

