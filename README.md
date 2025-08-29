# Transetu Task – Wind Farm Fault Detection

This repository contains my work for the Data Science open book assessment.  
The task was to detect faults in wind turbines using the **WindFarmC dataset**.  
I tried both **supervised** (Random Forest) and **unsupervised** (Isolation Forest) approaches and compared their performance.

---

## Dataset
- Dataset: WindFarmC (CSV file)
- Important columns:
  - `time_stamp` → time information
  - `status_type_id` → used to create the **target column**
  - Sensor values, power, wind speed, etc.

I created the `target` column where:
- `0` = normal state
- `1` = fault state (based on status_type_id)

---

## Preprocessing
- Removed unnecessary columns (IDs, non-numeric, etc.)
- Filled missing values using median
- Dropped constant columns
- Kept only useful sensor and power readings
- Split data into **70% training** and **30% testing**

---

## Models

### 1. Supervised (Random Forest)
- Trained with `target` labels
- Parameters: `n_estimators=200`, `class_weight=balanced`
- Metrics observed: **Precision, Recall, F1-score, False Alarm Rate**

### 2. Unsupervised (Isolation Forest)
- Trained only on normal data
- Detects anomalies as outliers
- Metrics compared against actual labels

---

## Results

- **Random Forest (Supervised)** performed better with higher precision, recall, and F1-score.
- **Isolation Forest (Unsupervised)** detected anomalies but had more false alarms.
- Final comparison plot shows that **Random Forest is the best choice** for this dataset.

---

## Files in Repo
- `TaskCodeAnalysis.ipynb` → Jupyter Notebook with code and plots  
- `TaskAssessmentReport.docx` → Report written in simple words (like student notes)  
- `README.md` → This explanation file  

---

## Conclusion
Based on the analysis, **supervised Random Forest** is the better approach for wind turbine fault prediction as it gives higher accuracy and more reliable results compared to unsupervised anomaly detection.
