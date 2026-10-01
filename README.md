# Healthcare Data Quality & Quarantine Pipeline

## 1. Project Overview
This project implements an automated, modular Python data pipeline designed to validate, sanitize, and process healthcare patient records. The pipeline evaluates incoming data batches against strict data quality dimensions and routes records to either a clean storage zone or a Quarantine zone for further investigation.

## 2. Problem Description
Healthcare organizations often process heterogeneous data batches with quality issues such as missing attributes, out-of-range values, duplicate records, or logical timeline contradictions. Passing unclean data to downstream medical analytics can lead to flawed insights and operational risks. This pipeline provides a quality gate mechanism to filter unreliable records automatically.

## 3. Data Source
- Synthetic/Mock Batch Healthcare Datasets containing attributes such as Patient ID, Age, Gender, Admission Date, Discharge Date, and Diagnosis.

## 4. Workflow / Architecture
1. *Data Ingestion*: Ingest batch files (e.g., CSV / Pandas DataFrames).
2. *Quality Gate Assessment*: Apply rule-based validations across multiple dimensions.
3. *Data Routing*:
   - *PASS*: Sent to the Clean/Trusted Delta Lake zone.
   - *FAIL*: Isolated into the Quarantine zone with error flags.
4. *Analytics Output*: Generate summary execution statistics and performance charts.
   Data Source
    │
    ▼
Ingestion (Batch Data)
    │
    ▼
Spark / Pandas Processing
    │
    ▼
Data Quality Engine (4 Checks)
    │
    ▼
   Quality Gate ──────────┐
    │                     │
  [PASS]                [FAIL]
    │                     │
    ▼                     ▼
Delta Lake            Quarantine
(Clean Zone)          (Isolated Data)
    │
    ▼
Analytics & Visualizations Output

## 5. Data Quality Checks
The pipeline implements the following checks:
- *Completeness*: Ensures mandatory fields (e.g., Patient ID, Admission Date) contain no nulls.
- *Uniqueness*: Detects duplicate Patient IDs.
- *Validity / Range Check*: Validates biological bounds (e.g., Age between 0 and 120).
- *Temporal Consistency*: Verifies chronological logic (Admission Date <= Discharge Date).

## 6. AI / RAG or Analytics Output
- Produces aggregated batch summaries and visualizations showing clean vs. quarantined record proportions to track data health over time.

## 7. Results
- Successfully routes valid records to the clean zone while preventing corrupted batch entries from entering production databases. Demonstration includes both passing and failing batch scenarios.

## 8. Technologies Used
- *Language*: Python 3.x
- *Data Processing*: Pandas, PySpark
- *Storage Layer*: Delta Lake
- *Visualization*: Matplotlib
## 9. How to Run the Project
1. Clone the repository:
git clone https://github.com/srhabdullatif-cell/Healthcare-Data-Quality-Pipeline.git
2. Install required packages (e.g., pandas, matplotlib, pyspark, delta-spark).
3. Open and execute the Jupyter Notebook (code file.ipynb).
## 10. Future Improvements
 Integrate automated email alerts for high quarantine rates.
 Add advanced anomaly detection using machine learning models.
 Build an interactive Streamlit dashboard for real-time quality monitoring.
## 11. SDAIA Academy GitHub Repository Link
 SDAIA Academy Organization: https://github.com/SDAIAAcademy
