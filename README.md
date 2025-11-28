# Data Pipeline Structure and Execution Guide

This README describes the folder structure, and the execution order of the data pipeline built around the medallion architecture (raw → bronze → silver → gold).

---

## 📁 Folder Structure Overview

```
/
├── Data/
│   ├── raw/                # Original, unprocessed input data
│   ├── bronze/             # Lightly cleaned data with minimal transformation
│   ├── silver/             # Standardized and validated data
│   └── gold/               # Final analytical datasets for reporting/ML
│
├── restructure_raw_data/
│   └── remove_exams_scores.ipynb             # Notebook for removing exam_score from raw data
│
├── bronze_layer_with_exam.ipynb        # Bronze pipeline for datasets with exam data
├── bronze_layer_without_exam.ipynb     # Bronze pipeline for datasets without exam data
├── silver_layer_with_exam.ipynb        # Silver pipeline for exam datasets
├── silver_layer_without_exam.ipynb     # Silver pipeline for non-exam datasets
└── gold_layer.ipynb                     # Final modeling/analytics dataset creation
```

---

## ▶️ Pipeline Execution Order

### **1. Bronze Stage**

1. Run both bronze notebooks:
   * `bronze_layer_with_exam.ipynb`
   * `bronze_layer_without_exam.ipynb`
2. Output is written into `data/bronze/`.

### **2. Silver Stage**

1. Run both silver notebooks.
   * `silver_layer_with_exam.ipynb`
   * `silver_layer_without_exam.ipynb`
2. Output is placed in `data/silver/`.

### **3. Gold Stage**

1. Run `gold_layer.ipynb`.
2. Output is stored in `Data/gold/`.

---

## Summary

* The project follows a clear medallion-lakehouse structure.
* Each notebook has a defined role in promoting data from raw → bronze → silver → gold.
* The execution order ensures reproducibility and clean separation of responsibilities.