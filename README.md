# Meta-Driven Medallion ELT Data Pipeline (Python)

[![Python Version](https://img.shields.io/badge/python-3.10%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

A scalable, configuration-driven, and robust **ELT (Extract, Load, Transform)** data pipeline built in Python. This project implements the industry-standard **Medallion Architecture (Bronze, Silver, Gold)**, entirely orchestrated and controlled via metadata configurations (JSON/YAML) rather than hardcoded logic.

---

## 🏗️ Architecture Overview
The pipeline processes data through three distinct refinement layers:

[ Raw Sources ] ──► [ Bronze Layer ] ──► [ Silver Layer ] ──► [ Gold Layer ] ──► [ BI & Analytics ]
                           
                           │
                           │
                           │
                           │
               [ Metadata Config (JSON/YAML) ]

*   **Bronze Layer (Raw):** Ingests raw data source files (CSV, Parquet, APIs, JSON) dynamically based on metadata definitions with minimal transformations, preserving history.
*   **Silver Layer (Cleansed):** Cleans data, standardizes schemas, handles null values, casts correct data types, and filters out or quarantines corrupted rows.
*   **Gold Layer (Curated/Aggregated):** Business-level aggregates, dimensional models, and analytics-ready datasets optimized for downstream BI and reporting tools.

---

## ✨ Key Features

*   **Metadata-Driven Engine:** Pipeline behavior (source mappings, transformations, target paths, and validation rules) is entirely controlled via configuration files. Add new pipelines without modifying core Python code.
*   **Modular Python Design:** Built using clean, object-oriented Python principles, making it easy to plug in custom sources, sinks, or transformation steps.
*   **Data Quality & Error Handling:** Automated checks, error logging, and quarantine pathways for invalid records.
*   **Extensible & Lightweight:** Can run locally or integrate seamlessly with workflow orchestrators (such as Apache Airflow, Prefect, or Dagster).

---

## 📁 Repository Structure

```text
meta-driven-medallion-elt/
│
├── configs/                  # Metadata configuration files (JSON / YAML)
│   ├── pipeline_config.json  # Schema mappings and pipeline control definitions
│   └── source_mapping.json   # Source-to-destination rules
│
├── src/                      # Core pipeline codebase
│   ├── __init__.py
│   ├── main.py             # Main execution framework engine
│   ├── extract.py            # Dynamic extraction logic (Bronze)
│   ├── transform.py          # Cleansing & business aggregation logic (Silver/Gold)
│   
│   
├
│
├── databin/
│ 
│
├── datalake/                     # Local data workspace (Ignored in git)
│   ├── bronze/
│   ├── silver/
│   └── gold/
│
│
├── logs/                    # Unit and integration tests
├── .gitignore
├── requirements.txt          # Python dependencies
└── README.md
