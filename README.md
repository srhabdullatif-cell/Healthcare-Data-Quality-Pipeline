# Healthcare-Data-Quality-Pipeline
# Healthcare Data Quality & Quarantine Pipeline

## Project Overview
This project implements an automated, modular Python data pipeline designed to validate, sanitize, and process healthcare patient records. The pipeline evaluates incoming data batches against strict data quality dimensions and routes records to either a clean *Delta Lake* storage zone or a *Quarantine* zone for further investigation.

## Pipeline Architecture & Features
- *Data Ingestion*: Reads batch patient datasets.
- *Data Quality Engine (HealthDataQualityEngine)*:
  - *Uniqueness Check*: Detects duplicate Patient IDs.
  - *Completeness Check*: Ensures mandatory fields (e.g., Name, Age, Admission Date) contain no nulls.
  - *Range Validation*: Validates biological/logical boundaries (e.g., Age between 0 and 120).
  - *Temporal Consistency*: Verifies chronological logic (e.g., Admission Date <= Discharge Date).
- *Data Routing*:
  - *Clean Zone (Delta Lake)*: Stores valid records matching all quality checks.
  - *Quarantine Zone*: Isolates failing/invalid records to maintain data health without blocking valid data flows.
- *Visualization*: Generates stacked bar charts representing clean vs. quarantined records per batch using Matplotlib.

## Tech Stack
- *Language*: Python 3.x
- *Data Processing*: Pandas, PySpark
- *Storage Layer*: Delta Lake
- *Visualization*: Matplotlib

## Execution & Testing
1. Run the main processing notebook/script to execute batch quality checks.
2. Review the output logs for PASS/FAIL batch evaluation.
3. Check generated plots to visualize pipeline routing performance.
