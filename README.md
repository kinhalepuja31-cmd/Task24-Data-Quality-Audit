# Task24-Data-Quality-Audit

**Project Overview**

  As part of my Data Analytics internship at Veda Technology, I designed and developed an Automated Data Quality & Validation Pipeline using Python.
  Raw business datasets often suffer from silent data corruption—such as chronological errors, broken relational links, and out-of-range financial inputs. This framework automates the detection of these anomalies across multi-sheet workbooks, translating programmatic checks into a standardized, human-readable Audit Summary Report and generating an isolated .csv issue   log for data engineering review.


**Tech Stack & Tools**

  •	Language: Python 3.x
  •	Libraries: Pandas, NumPy, OpenPyXL (Excel engine)
  •	Environment: Google Colab / Jupyter Notebook


** Dataset Structure**
 
The framework runs an end-to-end validation check across 3 interconnected sheets within the Global Superstore Excel workbook (containing 51,000+ total rows):
    1.	Orders Sheet: Master transaction records (24 columns tracking dates, shipping, sales, and profit).
    2.	Returns Sheet: Relational log capturing returned transactions by Order ID.
    3.	People Sheet: Master data containing regional manager assignments (Person vs. Region).


**Automated Quality Rules Enforced**

The script implements an automated logging system (log_issue()) that evaluates seven structural and business-logic rules:
  1. Structural Checks
     •	Duplicate Rows: Flags full-row duplicates across the dataset.

     •	Missing Values: Scans and reports missing entries in mission-critical columns (Order ID, Order Date, Customer ID, Sales, Quantity).
  3. Business Logic & Range Validation
     •	Quantity Integrity: Flags rows where the unit quantity is ≤ 0.

      •	Sales Integrity: Identifies entries containing zero or negative financial transaction figures.
  4. Chronological Consistency
     •	Timeline Validation: Flags logical timeline violations where Ship Date occurs prior to Order Date.
  5. Relational & Master Data Integrity
     •	Orphan Records: Performs cross-sheet checks to isolate Returned Order IDs that do not exist in the master Orders dataset.
 
     •	Master Data Validation: Verifies that geographical strings in the transaction data accurately match valid entries in the People master table (preventing typos and regional mapping drift).

**Key Learning Outcomes**


  •	Defensive Pipeline Engineering: Moving past basic manual exploratory data analysis (EDA) to write robust, reusable verification rules.
  •	Relational Validation: Managing cross-table consistency constraints similar to relational database primary/foreign key requirements.
  •	Production Readiness: Packaging data pipelines to cleanly output structural status reports and error matrices, mimicking real-world data engineering workflows.


