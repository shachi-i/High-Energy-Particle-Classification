
# Lepton Classification with Machine Learning 

This project focuses on classifying high-energy forward leptons using particle physics data from CERN's ATLAS detector. We transform ROOT-format physics data into machine learning-ready CSVs, perform extensive preprocessing and feature engineering, and train classifiers to detect high-energy forward leptons.

---

## 📌 Objective

To build a binary classification model that identifies **high-energy forward leptons** from CERN ATLAS Open Data based on energy, pseudorapidity, and transverse momentum features.

---

## 🧰 Tools & Libraries
- `uproot`, `awkward`, `numpy`, `pandas` – for reading & cleaning ROOT data  
- `matplotlib`, `seaborn` – for visualization  
- `scikit-learn` – ML preprocessing and evaluation, Random Forest, XGBoost  
- `xgboost` – gradient boosting classifier  
- `imbalanced-learn` – for SMOTE balancing  
- Google Colab – cloud-based development

---
## 🧪 Dataset

- Source: [ATLAS Open Data (8 TeV Egamma)](https://atlas-opendata.web.cern.ch/Legacy8TeV/Data/DataEgamma.root)  
- Total events after filtering: **58,671**
- Class distribution:
  - `0`: 51,749 (non-forward/non-high-energy leptons)
  - `1`: 6,922 (high-energy forward leptons)

---

## 📊 Data Preprocessing
- Extracted data from `.root` file using `uproot`
- Converted awkward arrays and cleaned nested structures
- Saved as `.csv` to simplify further processing
- Performed imputation, encoding, normalization
- Created binary classification label: `high_energy_forward_lepton`
- Imputed missing values using `SimpleImputer`
- Balanced class labels using `SMOTE`
- Standardized features

---
## 🎯 Label Definition

A **high-energy forward lepton** is defined as:
- `lep_E` > 100000
- `|lep_eta|` > 1.0
- `lep_pt` > 40000

Label column: `high_energy_forward_lepton`

---
## 🧪 Models & Results

| Model                 | Accuracy | Precision (class 1) | Recall (class 1) | F1-score (class 1) |
|----------------------|----------|----------------------|------------------|---------------------|
| Random Forest         | 88.2%    | 0.51                 | 0.33             | 0.40                |
| XGBoost (imbalanced)  | 16.2%    | 0.12                 | 0.95             | 0.21                |
| XGBoost (SMOTE tuned) | 37.9%    | 0.13                 | 0.76             | 0.22                |

> Baseline model showed very high precision (99.5%) due to class imbalance — post-SMOTE, results became more realistic.

---

## 📌 Observations
- Class 1 (target) is highly imbalanced (6,922 vs 51,749)
- SMOTE significantly improved minority class recall
- Most important features: `lep_pt`, `lep_E`, `lep_eta`, `lep_charge`, jet-related features

---

## 🧾 Conclusion
This project showcases end-to-end ML workflow using real scientific data, demonstrating the feasibility of applying data science and classification techniques to particle physics.

---

## 📄 Medium Article
👉 [Link to the detailed write-up](#coming-soon)
